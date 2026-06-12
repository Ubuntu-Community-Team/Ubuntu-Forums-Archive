---
title: "Cinnamon Taskbar SIze &amp; menu translation"
date: 2012-08-28
forum: Desktop Environments
---

### Post by mascir on 2012-08-28
Hi All,

i have installed Cinnamon desktop manager on my 12.04 box.

Nice look, nice function but 2 issues...

1) the size of the taskbar (bottom position) is too small for my monitor resolution (i have 26" with 1920×1080).

2) some voice of start menu have not been translated, remained in English. I tried to download the italian language pack...KO.

Questions:

1) Is it possible to resize the taskbar? If yes...how?

2) Is it possible to translate all the menu? If yes...how?

cheers.

---

### Post by mascir on 2012-08-29
FIXED!


open the terminal and put the command

sudo gedit /usr/share/cinnamon/theme/cinnamon.css

then, search for this following section:

#panel {
    color: #ffffff;
    background-color: #555555; 
    font-size: 12pt;          
    font-weight: normal;
    height: 32px;
}

so, i have modified both "font size" (12px - was originally 8.5px) and "height" (32px - was originally 25px)

in case of other themes search for home/.themes folder and edit the "theme name" css

looking like this following lines

#panel {
background-gradient-direction: vertical;
background-gradient-start: rgba(39,39,39,0.7);
background-gradient-end: rgba(21,21,21,0.7);
border: 1px solid rgba(0,0,0,0.6);
box-shadow: 0px 0px 3px 2px rgba(11,11,11,0.5);
border-top: 0px;
border-left: 0px;
border-right: 0px;
color: #eee;
font-size: 9.5pt; 
font-weight: bold;
height: 2em;

for the status icon:

.system-status-icon {
icon-size: 1.15em;

This is best fit for my eyes :lolflag:

see ya!

---

