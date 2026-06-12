---
title: "Enable Dual Displays or More in Ubuntu (NVIDIA)"
date: 2009-05-03
forum: General Help
---

### Post by PAtechie on 2009-05-03
[SIZE=5][FONT=Nimbus Sans L, sans-serif][SIZE=3]When you boot up, if you haven't done so already, you should see a little      icon in      the top bar (Says Applications, Places, System, etc.) looking like an      internal card for a computer or a form of a “computer chip”. Click on that and     enable the driver that is the newest one, or is recommended. After you are done     with that click system in the top bar, then administration, then NVIDIA X Server      Settings. If it is not there, open up the terminal and type: [/SIZE][/FONT][FONT=AR PL UMing CN][SIZE=3]sudo apt-get install     nvidia-settings[/SIZE][/FONT][FONT=Nimbus Sans L, sans-serif][SIZE=3]. That should install the NVIDIA X Server Settings. Then, open      up the NVIDIA X Server Settings, and click X Server Display Configuration.      Enable the additional display(s) the way you want to in TwinView, then click     apply. You should get your additional display(s) showing now. Afterwards, click     the save to X configuration file button and uncheck “Merge with existing file.”.     Then click the show preview button, select all the text, and copy it. When your     done with that, open up the terminal and type in: [/SIZE][/FONT][FONT=AR PL UMing CN][SIZE=3]gksudo[/SIZE][/FONT][FONT=Nimbus Sans L, sans-serif][SIZE=3]. Make sure it says root     underneath “as user:”, and then in the box underneath “Run” type [/SIZE][/FONT][FONT=AR PL UMing CN][SIZE=3]gedit[/SIZE][/FONT][FONT=Nimbus Sans L, sans-serif][SIZE=3]. Paste     your text you had previously copied in the text editor and click “Save As” under     “File”. Then click “browse for other folders”, then file system in the left bar, then     “etc”, then “X11” then click [/SIZE][/FONT][FONT=AR PL UMing CN][SIZE=3]xorg.conf[/SIZE][/FONT][FONT=Nimbus Sans L, sans-serif][SIZE=3], then overwrite the file by clicking save.     After that's all done, Close all open windows, and restart. When you login, your     additional display(s) should be up and running for immediate use of all your     needs.[/SIZE][/FONT][/SIZE]




[RIGHT][SIZE=5][FONT=Nimbus Sans L, sans-serif][SIZE=3]Ben Chapman[/SIZE][/FONT][/SIZE]
[SIZE=5][FONT=Nimbus Sans L, sans-serif][SIZE=3]patechie@gmail.com[/SIZE][/FONT][/SIZE]
[SIZE=5][FONT=Nimbus Sans L, sans-serif][SIZE=3]5/3/09
[/SIZE][/FONT][/SIZE][/RIGHT]

---

