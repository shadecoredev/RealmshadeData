# Realmshade Data
This repository contains all resource files for the game Realmshade.

## Adding new language translation
1. To propose a new language translation, first look for an existing fork for your language, or create a new fork. I recommend including language name in the fork title.
2. Locate the directory `data/translations` and duplicate the file `english.csv`. Rename the file to indicate the lanuage, for example `german.csv`.  
3. Read the [CSV translation information](#csv-translation-information) section and edit the newly created file accordingly.  
Example `english.csv`:
    ```csv
        ,en_US
        LANGUAGE_NAME,English
        UI_TUTORIAL,Tutorial
        UI_PLAY,Play
        ...
    ```
    Edited version `german.csv`:  
    ```csv
        ,de_DE
        LANGUAGE_NAME,Deutsch
        UI_TUTORIAL,Tutorial
        UI_PLAY,Spielen
        ...
    ```
    Make sure to not to add or remove any lines. The resulting CSV must contain the exact same line count as the original `english.csv`. 
4. To add a tranlation to individual items and events, open the directory `data/items` or `data/events`. Each subdirectory contains a JSON file with a key `translation` at the botton of the file. The English name for any item and event is the file name capitalized. Add a new key with your locale, same that you use in CSV file.  
Example `apple.json`:
    ```json
    ...
    "translation" : {
            "ru_RU" : "Яблоко"
        }
    ...
    ```
    Edited version `apple.json`:
    ```json
    ...
    "translation" : {
            "ru_RU" : "Яблоко",
            "de_DE" : "Apfel"
        }
    ...
    ```

## CSV translation information
First line of the CSV file contains a comma ',' and a locale code. Choose appropriate locale code for your translation based on this documentation: https://docs.godotengine.org/en/stable/tutorials/i18n/locales.html

Each line of the CSV file contains a key, followed by a comma ',' and a key translation.  
Keys have a format: `<TAG>_<NAME>(_MSG)`  
`<TAG>` is a single word that represents a context for the text.  
`<NAME>` represents either english text that can be translated directly (if no suffix `_MSG` present), or a name for the message.  
To translate keys that end with `_MSG` you must refer to `english.csv` to see the original message.

Sometimes a message text contains a character sequence like this: `%s`, `%d`, `%%`.
This sequence represents a placeholder for another text or value. Make sure to not edit or remove this placeholder in the resulting translated text.

## License
Source code is licensed under MIT license.

All image files are distributed under "All Rights Reserved".  
Copy and distribution of images without my explicit permission is strictly prohibited.  

Copyright (c) 2026 shadecore_dev