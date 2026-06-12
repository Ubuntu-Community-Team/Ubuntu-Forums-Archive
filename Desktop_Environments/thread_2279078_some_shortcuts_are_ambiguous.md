---
title: "some shortcuts are ambiguous"
date: 2015-05-20
forum: Desktop Environments
---

### Post by z-mail-i on 2015-05-20
hello community,

i get the this message in kate and some other programs (system settings, muon discover)
 > The key sequence 'Ctrl+Q' is ambiguous. Use 'Configure Shortcuts'

 from the 'Settings' menu to solve the ambiguity.

 No action will be triggered.


in kate about all default shortcuts are generating the ambiguous-message.

the system is installed two days ago - 
but i first installed a ubuntu 15.04 64bit (with an separate partition for home) and after this installed kubuntu 15.04 64bit (fresh formated root but reused the home partition)
so eventually the previous ubuntu installation left some shortcut bindings in my configs?

in my user configs (system settings - shortcuts) i can't find ambiguous definitions.
i also tried to reset the shortcuts do the 'defaults' but that did not changed it.

i tried with a second test user and there all shortcut worked.

are there other options to 'reset' all shortcut in my current user?

thanks for your help
sunny greetings
stefan

PS: its really hard to use a text-editor when Ctrl+S and so one are not working... ;-)

---

### Post by speartip on 2015-05-21
Its probably the way that you installed using an existing Home partition that's the issue, causing a conflict of config files.
That's why when you created a 2nd user it works fine, they have there own Home partition.
What I always do on a fresh install when keeping my existing Home partition, is to delete all the hidden files first, and just keep my data.
You could delete all the hidden files & reboot, that would probably resolve your issue, but give you a vanilla Desktop that you would have to set up again.

---

### Post by z-mail-i on 2015-05-21
hi speartip,
thanks for the explanation :-)
i think as last step i could try the 'delete all config files' idea-
i would like to reset only shortcut things... ;-)
is  there somewhere a overview what config files are involved with shortcut  mappings in kubuntu and ubuntu? (so i can only delete them...)

thanks for your help!
stefan

---

### Post by speartip on 2015-05-21
Not too sure. Most configs are in .config, .kde or .local/share.
You could try renaming them, one by one, so that after a reboot a fresh config file is created, & then you can see what folder the problem is in.
If that doesn't resolve it delete the new folder & rename the old folder correctly again, to get your old configs back.
I can't offer too much help because you are using plasma 5, I still use the 14.04 LTS.

---

### Post by z-mail-i on 2015-05-21
hi speartip,
i think i have to do a real fresh install... have screwed up more stuff....
i tried and renamed 
 [FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]~/.config [/COLOR][/FONT]khotkeysrc
[/COLOR][/FONT] [FONT=monospace][COLOR=#000000]~/.config kglobalshortcutsrc[/COLOR]
[/FONT]
(i renamed with 'OLD__' as prefix)
but after my restart my desktop (background image and mainmenu / taskbar) was gone


i had luck and one of my startup programs (a filemanager) had a button to open a terminal.
i looked in the folder and the kglobalshortcutsrc was generated. the other feil missed.
i fired up kate from the terminal and tried - the shortcut ambiguous was still there -
so this thing is stored somewhere else...
i renamed the OLD__xxx to the original names and restarted in the hope that all came back - but i think i have mixed up some other things in the first try...

i think the easiest is just to backup interesting files to an external disc (firefox profile for example)
and than do a complete fresh install..
sadly yesterday i was ad the point i had the feeling that i have installed all needed packages/programs...
so will have to do this all again...

---

### Post by speartip on 2015-05-21
You shouldn't need to do a fresh install. Just delete all the hidden folders in your home folder, except .mozilla and reboot. You should have a new desktop, but with all your apps still installed.

---

### Post by z-mail-i on 2015-05-22
hi speartip,

your right - alternative i can also just create a new fresh user .. (than i only have to copy the configs i want to have.)
i was overreacting yesterday... sorry
i will try the your method...

---

### Post by z-mail-i on 2015-05-22
i logged in as my testuser and then 
renamed all .files and all .folders from my main user (prefixed them with 'OLD')
then restarted the system and logged in as my main user.
and TADA its all fine again! the shortcuts are working again!!
thanks speartip for your help!!!

---

### Post by speartip on 2015-05-22
Good to hear you're sorted.
If my system screws up, I generally delete my .kde & .config folders, then run bleachbit & reboot.
It means resetting all my preferences, but that is usually only 10 mins, & system runs smoothly again.

---

