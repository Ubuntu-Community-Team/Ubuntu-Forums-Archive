---
title: "devilspie firefox problem"
date: 2008-03-07
forum: Desktop Environments
---

### Post by meg23 on 2008-03-07
I am using the latest version of devilspie on gutsy gibbon. Yesterday I was able to get firefox to work with devilspie, however something stopped working and now it 

can't find the window and I guess metacity is taking over and placing the window in the top left corner. I am not using compiz or any other window manager. I basically 

just want the window to attach to the top right corner of the screen. I am using it to manage a thunar window and devilspie is working successfully. 

Here is my config file for firefox-bin.ds:

(if
(is (application_name) "firefox-bin")
(begin
(set_workspace 1)
(geometry "1100x700+700+0")
)
)

Any clues?

---

