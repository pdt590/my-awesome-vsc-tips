# Visual Studio Code Tips

- Enable multiple tabs
  ```
  "workbench.editor.enablePreview": false
  ```
- Disable mini map
  ```
  "editor.minimap.enabled": false
  ```
- How to integrate Latex editor on vsc
  - Download and install Miktex
  - Install [LaTeX Workshops](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) plugin
  - In setting.js
    ```js
    "latex-workshop.latex.recipes": [{
      "name": "texify",
      "tools": [
        "texify"
      ]
    }],
    "latex-workshop.latex.tools": [{
      "name": "texify",
      "command": "texify",
      "args": [
        "--synctex",
        "--pdf",
        "--tex-option=\"-interaction=nonstopmode\"",
        "--tex-option=\"-file-line-error\"",
        "%DOC%.tex"
      ]
    }]
    ```
  - Conflicted plugins: `Markdown+Math`; `latex-formatter`
- Get plugins info
  ```bash
  code --list-extensions > vs_code_plugins.txt
  ```
- Install plugins
  ```bash
  code --install-extension .........  # Install a packet
  ```
- VSC for arduino
  - [intellisense works out of the box](https://github.com/Microsoft/vscode-arduino/issues/438)
  - Force Intellisense to use the "Tag Parser"
    ```js
    // User Settings 
    "C_Cpp.intelliSenseEngineFallback": "Disabled",
    "C_Cpp.intelliSenseEngine": "Tag Parser",
    
    //c_cpp_properties.json
    {
      "name": "Arduino",
      "includePath": [
        "${workspaceRoot}"
      ],
      "browse": {
        "path": [
          "D:/Program Files (x86)/Arduino/hardware",
          "D:/Program Files (x86)/Arduino/libraries",
          "D:/Users/Julian/Documents/Arduino/libraries/",
          "D:/Users/Julian/Documents/Arduino/hardware/",
          "${workspaceRoot}"
        ],
        "limitSymbolsToIncludedHeaders": true,
        "databaseFilename": ""
      },
      "intelliSenseMode": "msvc-x64"
    }
    ```
  - Note
    - [How do I get IntelliSense to work correctly](https://code.visualstudio.com/docs/cpp/faq-cpp#_how-do-i-get-intellisense-to-work-correctly)
    - [Arduino: The system cannot find the file specified error](https://stackoverflow.com/questions/49970235/arduino-the-system-cannot-find-the-file-specified-error)
    ```
    That way, only the Tag Parses will be used as the engine and the config in the c_cpp_properties.json becomes a lot 
    simples, since intellisense reads directories recursively now. That way I also got the engine to read libraries I 
    installed manually, since they are placed in my homedirectory (D:/Users/Julian/Documents/Arduino/libraries/). 
    Same goes for boards I installed, like the ESP8266, which has its package sit in "D:/Users/Julian/Documents/Arduino/hardware/".
    ```
   

