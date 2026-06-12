---
title: "installing apps"
date: 2008-05-12
forum: Desktop Environments
---

### Post by 64dragon on 2008-05-12
i'm new to linux and installed 64bit ubuntu yesturday. i'm trying to install something that will display my temps and other info. i installed lm sensors and went thru all that yesturday but i'm having trouble installing a front end. 

i "installed" a few things thru synaptic but theres no icons in the app menu. how do i acess these programs? 
one of the items i "installed" was gkrellm and i found that i can type that into terminal and it will launch but once it closes it doesn't save what i changed. 
i found another program, screenlets and there's a widget? in there that is a sysmonitor, i'd like to edit what it displays and found the file but am unable to save it after i made changes. it says that i don't have permission to save it in that location. how can i sudo and save to where the file needs to be? or how can i edit the file, save it to desktop and move it to where it needs to be in usr/share/screenlets

---

### Post by NikoC on 2008-05-13
Well, when you press ALT + F2 a dialogue box will appear in which you can type the program you want to run...

If you want to run it as sudo, then in the dialogue box type 'gksudo application_name' which is basically the same as typing 'sudo application_name' in a terminal window, but now you will get another dialogue box in which you can type your pass.

You could also right click on the main menu in the gnome application bar and edit it: this way you can add, remove or change programs as you please.

For the second question: in a terminal type:
sudo gedit /usr/share/screenlets/filename_you_want_to_edit

Other option: create the file (e.g. using gedit), save it to your desktop and then copy it to the destination folder by typing in a terminal:
sudo cp filename /usr/share/screenlets/filename

Hope this helps you out.

edit: I'm not sure if you already found out but using the tab key autocompletes directory and file names which makes it a lot easier to handle them

---

