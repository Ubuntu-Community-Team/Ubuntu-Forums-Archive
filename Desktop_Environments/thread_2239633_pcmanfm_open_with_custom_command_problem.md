---
title: "pcmanfm open with custom command problem"
date: 2014-08-14
forum: Desktop Environments
---

### Post by budgerigar on 2014-08-14
Hello.

I've been using Ubuntu for a few years, Lubuntu for nearly two years and I've not found a problem I can't fix without just a bit of googling (often finding the answer on ubuntuforums). However, I installed Lubuntu 14.4 from scratch a couple of days ago and I have run into a problem I didn't have with my previous 13.10 installation:

In pcmanfm, I want to be able to open .mng animations by default with the command

animate -dispose 2 %f

Animate is part of imagemagick. I can open these files from the terminal without a problem. I have tried:
right click > open with > custom command line
right click > properties > open with > customise

I have tried with and without "execute in terminal emulator", and both with and without including "animate" in the "applicaton name" box. But this doesn't change which application does open .mng files. I can only change it to other programs listed in "Installed Applications", where animate doesn't appear, probably because it is a command line program without a full GUI.

I notice there are a few options in Edit > Preferences > Advanced, but I don't really understand them.
I have also looked at ~/.local/share/applications/mimeapps.list, where video/x-mng is not listed. Should I add something here?

Any help would be appreciated.

---

### Post by mc4man on 2014-08-15
your issue is that while pcmanfm creates a custom command launcher (userapp-xxx-XXXXXX.desktop it doesn't add it to mimeapps.list so it won't show up.

So open ~/.local/share/applications, find the custom command .desktop it created & use it's actual name in mimeapps.list either in the Added section or in both the Added & Default sections. Added section uses ; after an entry, Default doesn't.

I don't use lubuntu or pcmanfm in general but maybe the 2 screens can help
scr. 1 - I've highlighted the .desktop pcmanfm > Open with > Open with.. > Custom Command line created. 
scr. 2 I added the above .desktop to a mimeapps line for mp3

After adding then that .desktop will show in pcmanfm's context menu > open with on .mp3's using the name chosen when creating 
(- the actual name of the .desktop, (used in mimeapps.list),   is not the same of the name you gave it when creating, that's determined by this line in the .desktop
Name=

---

### Post by vasa1 on 2014-08-15
> **budgerigar said:**
> ..., I installed Lubuntu 14.4 from scratch a couple of days ago and I have run into a problem I didn't have with my previous 13.10 installation:
...
BTW, pcmanfm in 14.04 is version 1.2 and it is substantially different from earlier versions. Please take a look at [http://wiki.lxde.org/en/PCManFM](http://wiki.lxde.org/en/PCManFM) and [http://ubuntuforums.org/showthread.php?t=2231186](http://ubuntuforums.org/showthread.php?t=2231186)

---

### Post by budgerigar on 2014-08-17
Thanks for your replies.

I added:
video/x-mng=userapp-animate-CX0ZKX.desktop;

Now animate appears as an option when I right click. However, it opens a terminal, which does nothing. I check the process id of animate, and that shows that the program isn't running. Running pcmanfm from a terminal shows that it does launch a terminal, but says nothing of any processes it might try to start. It looks like I'm a step closer to making this work, but not there yet. I've just tried messing around with custom actions mentioned in [http://ubuntuforums.org/showthread.php?t=2231186](http://ubuntuforums.org/showthread.php?t=2231186), but none of these are working for me. Maybe things have changed that no-one has really explained yet, such as where the scripts and/or .desktop files should be.


I usually use midnight commander as my file manager, but I need pcmanfm for browsing picture and video files.

---

### Post by budgerigar on 2014-08-17
I have just tested this on a fresh install of Fedora with LXDE running on VirtualBox. Here I have the same problem, although here, pcmanfm does add lines to the mimeapps.list file, so at least on Fedora, I don't have to mess about with editing text files just to see that it doesn't work. Could this be a pcmanfm bug?

---

### Post by mc4man on 2014-08-17
Well the terminal would only show anything produced after the command is run & would close when the command exits, ie. when animate is done.
(- that would be the default profile here for gnome-terminal.

I don't happen to have any .mng's lying about but testing this from one I found attached to a Firefox bug it *seems* to work ok (??
(- the .mng opens, animates, then exits

So does animate  work on same file from a terminal?, and why do you need a terminal when opening from a file browser?

Attached very short vid showing, added -verbose to launcher command to illustrate terminal behavior

---

### Post by budgerigar on 2014-08-18
The animate command works fine from the terminal.

I just tested setting the command

echo %f > %f_test.txt

as the default command to execute for .mng files. I assumed that this should create a new text file in the directory I launch the .mng from. Again, a terminal opened, but no command was executed. It didn't create a new file.

The next test was to set leafpad as the default application. This time I assumed that leafpad would open and try to display the entire .mng file as plain text gibberish. It actually opened with only two lines: &#352;MNG followed by a symbol that shows it didn't understand the encoding. This is the same behaviour as trying to open the file with leafpad from the terminal. So although it didn't behave quite the way I expected, it did update the mimeapps.list and it actually did *something*.

It seems there are two problems:
When setting a command-line application to open a file type, it doesn't automatically update mimeapps.list
After updating mimeapps.list manually, the option is added to the right-click menu, but it doesn't perform the command.

I never had this problem with Lubuntu 13.04 or 13.10. I installed Lubuntu 14.04 from scratch rather than upgrade from the previous version.
I wouldn't normally want a terminal to open each time I open this file type. This was just part of my test to see if pcmanfm is trying to do anything.

---

### Post by budgerigar on 2014-09-10
It's taken a long time of not really doing anything about this problem, but eventually I found an answer that works. It's not ideal because if a program or operating system offers to do something, it should be able to do it. The only thing that should stop it from working would be very poor hardware capabilities (not relevant in this case) or the user having meddled with things. I haven't had the chance to make a mess of my operating system yet. It was a fresh install. However...

After creating an entry in ~/.local/share/applications by doing what pcmanfm asked to do, I had a file: '~/.local/share/applications/userapp-animate -dispose 2-VDUHMX.desktop'.

code:
xdg-mime default 'userapp-animate -dispose 2-VDUHMX.desktop' video/x-mng

The xdg-mime command might work without reference to this file or the special 'VDUHMX' thing that I don't see the point of, but I haven't tested this.

---

