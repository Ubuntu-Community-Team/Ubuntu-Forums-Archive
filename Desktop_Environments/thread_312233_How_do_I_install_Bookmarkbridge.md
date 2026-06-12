---
title: "How do I install Bookmarkbridge?"
date: 2006-12-04
forum: Desktop Environments
---

### Post by lukon on 2006-12-04
I'm a linux newbie who has no idea how to complete this installation process for the application I just got via the GUI synaptic, called "bookmarbridge"

The package now supposedly installed, I can't find it anywhere in my menus to run it. Perhaps there are more steps involved in installing it, steps I know nothing about.

The final post in this thread here gives a clue, but not a clue good enough to help me out: [http://www.ubuntuforums.org/showthread.php?t=34367&highlight=bookmarkbridge](http://www.ubuntuforums.org/showthread.php?t=34367&highlight=bookmarkbridge)

So, do I have some "compiling" to do or what?

---

### Post by Gillingham on 2006-12-04
Hi, I suspect you have installed it, have you tried running it from the command prompt?  I'd guess the command would be bookmarkbridge, but am not certain.  If you have installed it via synaptic you shouldn't have to compile it.

If this works you can add it to your menus via the menu editor (alacarte) which I can't remember where it is under dapper.

---

### Post by lukon on 2006-12-07
Ok. 
 
So on a hunch I just typed in the string "bookmarkbridge", and here's the terminal output: 
 
------------------------------------------------------- 
 
luke@Axiom:~$ bookmarkbridge 
X Error: BadDevice, invalid or uninitialized input device 166 
Major opcode: 144 
Minor opcode: 3 
Resource id: 0x0 
Failed to open device 
X Error: BadDevice, invalid or uninitialized input device 166 
Major opcode: 144 
Minor opcode: 3 
Resource id: 0x0 
Failed to open device 
 
------------------------------------------------------ 
 
But after the terminal spit that out, bookmarkbridge did open it's main window, to my surprise. 
 
So I went to the settings window and sew that it had not detected my Firefox installation. 
 
So I attempted to add it manually as "Mozilla Browser". 
 
Then I went back to the main window to add the Mozilla Browser to my "Selected Source Browsers" and "Selected Destination Browsers". 
 
Then I hit the "View" (View bookmarks in source browsers) action button and got an error message saying "The Mozilla bookmarks could not be found", and the details of which said "The error occured on line 806 of Mozilla.cpp" 
 
---------------------------------------------------- 


      RE: Installation failure on Ubuntu Dapper Dra
      By: lukon (lukon) - 2006-12-07 05:24
      Ok, in spite of the error messages I encountered above, it is possible to get Bookmarkbridge working in ubuntu Dapper Drake. 
       
      After installing BMB using the GUI package installer supplied with ubuntu, you need to start BMB by using the command prompt. Get to the command prompt through the following menu path (That is, if you haven't changed your menus around yet.): 
       
      “Applications>Accessories>Terminal” 
       
      At this command prompt, type: 
       
      bookmarkbridge 
       
      and hit the “enter” key. 
       
      Error messages will appear in the terminal window. Ignore them. Then the BMB main window will appear. 
       
      Now BMB needs to have your browsers entered into it. So mouse-click BMB's “Settings...” button. 
       
      The settings window appears. 
       
      Now mouse-click the setting window's “Add” button. 
       
      A browser menu sub-window appears. 
       
      Now pick one of the browsers you want to include in BMB's synchronizing. 
       
      The remaining instructions pertain specifically to sharing/synchronizing bookmarks between two browsers on a dual boot, WIN98se/ubuntu system. MS IE is on the WIN98se side, installed on drive C. Mozilla FireFox is on the ubuntu side, installed on some other physical hard drive. 
       
      The first browser we'll include will be Mozilla Firefox. So in the browser menu sub-window, mouse-click the name “Mozilla Browser” to highlight it. Now mouse-click the “OK” button. 
       
      The browser menu sub-window disappears and the entry “Mozilla Browser Mozilla Browser Bookmarks” appears in the settings window. 
       
      Now you need to tell BMB the directory path to the FireFox bookmarks. 
       
      Mouse-click the entry “Mozilla Browser Mozilla Browser Bookmarks” to highlight it. 
       
      Mouse-click the “Browse...” button. 
       
      The “Select Your Bookmarks File” sub-window appears. 
       
      The file structure shown in this sub-window cannot help you navigate to the Firefox bookmarks. Do not waste your time trying to navigate to it. (FireFox bookmarks are in “hidden” directories that MBM's directory browser cannot access.) You need to type the directory path into the “Look In:” text box. 
       
      But first, you will need to do more research to discover this directory path. The path has a slightly different name for each computer user. So here's how to research it: 
       
      Open the ubuntu file browser (usually the nautalis thing) via the following menu path: 
       
      Places>Home Folder 
       
      The window for your home folder appears. The name of your home folder is part of the directory path you need. In fact, the first part of the directory path is: /home/”name of your home folder”/ 
      The name of my home folder is: lukon. So I'll use lukon in further examples. Like this: /home/lukon/ 
       
      Now in this file browser window, mouse-click the “View” pull-down menu control and then click the “Show Hidden Files” menu item to reveal the hidden files in your home folder. One of these hidden files should be a directory called “.mozilla” Double-mouse-click it to open it. Now double-mouse-click the “firefox” folder. 
       
      Now find the folder that has for it's name a string of characters and “.default” at the end. Mine says “jj51srqx.default” but yours will say something else for “jj51srqx”. This folder's name is also part of the needed directory path, which can now be completed thus: /home/lukon/.mozilla/firefox/jj51srqx.default/ 
       
      Now close the computer's file browser and return to BMB's “Select Your Bookmarks File” sub-window. 
       
      Mouse-click the “Look In:” text box and type the following into that textbox: 
       
      /home/lukon/.mozilla/firefox/jj51srqx.default/ 
       
      ...where “lukon” is YOUR home folder name, and “jj51srqx” is part of YOUR funny firefox folder name. 
       
      NOTE: I had some trouble getting this directory path accepted by this BMB sub-window. The trouble now is, I forgot the nature of the problem and how I got it to finally work. It may have had something to do with either hitting the “return” key after the typing, or not. Just keep trying until it sticks. 
       
      Now mouse-click the “File Name:” text box and type: bookmarks.html 
       
      Now mouse-click the “Open” button. 
       
      The sub-window disappears. 
       
      Now let's do it for the IR browser on the WIN98se side. 
       
      Now mouse-click the setting window's “Add” button. 
       
      The browser menu sub-window appears. 
       
      In the browser menu sub-window, mouse-click the name “Internet Explorer” to highlight it. Now mouse-click the “OK” button. 
       
      The browser menu sub-window disappears and the entry “Internet Explorer Internet Explorer Bookmarks” gets added in the settings window. 
       
      Mouse-click the entry “Internet Explorer Internet Explorer Bookmarks” to highlight it. 
       
      Mouse-click the “Browse...” button. 
       
      The “Select Your Bookmarks File” sub-window appears. 
       
      Mouse-click the “Look In:” text box and type the following into that textbox: 
       
      /media/c_drive/windows/Favorites/ 
       
      ...where “c_drive” is the name given to your WIN89 system drive C as it appears on your ubuntu desktop. This name got assigned to that drive when someone followed a procedure for making your WIN98 C drive automatically mounted and read/writable at ubuntu boot-up. See this link for that proceedure: 
       
      [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html) 
       
      (And yes, that does say “widows” instead of “winDows” in that link.) 
       
      And this directory path is for WIN98 only. XP has a different one that I don't know, but looks something like: /media/c_drive/documents_and_settings/blah blah... 
       
      Now mouse-click the “Open” button. 
       
      The sub-window disappears. 
       
      Yay! Now BMB has the info it needs to do its work. So mouse-click the “Ok” button. The main window re-appears. 
       
      Now add the two browsers to the “Step 1: Select Source Browsers” and “Step 2: Select Destination Browsers” item boxes and just push the buttons you like. (I'm now too tired to hold you by the hand on this part.) 
       
      OK. Now comes the part you're going to hate me for. 
       
      When you finally get around to mouse-clicking the “Merge...” button, you'll likely get an error message, something to the effect of “could not write to bookmark.xxx file”. You'll notice that this is a file within BMB's own structure, and not with any of the web browsers. Anyway, this error has to do with an abuntu security restriction, I suspect. To avoid this restriction, start BMB at the command prompt with the “sudo” word in front. That means at this point you must shut down BMB and re-start it by typing:  
       
      sudo bookmarkbridge 
       
      ...and then entering your password when it then prompts you for it. 
       
      Now you can do the merging without the error, I think. Well, that worked for me anyway. 
       
       
      NOTE: Some IE bookmarks do not get transferred to FireFox in the merge process. These bookmarks tend to be the ones IE has pre-loaded when you install IE, like MSN and stuff.

---

