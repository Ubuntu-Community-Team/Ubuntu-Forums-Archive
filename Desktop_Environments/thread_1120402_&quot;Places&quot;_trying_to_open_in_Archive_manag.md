---
title: "&quot;Places&quot; trying to open in Archive manager"
date: 2009-04-08
forum: Desktop Environments
---

### Post by Dazwhite on 2009-04-08
Hi all,

Not too sure what I did but now when I go to the "places" menu it is trying to open in archive manager and says "archive type not supported".

How do I fix this?

Thanks!

---

### Post by Dazwhite on 2009-04-08
Nevermind... Figured it out. In case anyone else runs into this issue do the following...

Press alt+F2 type nautilus and click run.

Right click any folder and click properties.

Click the open with tab and make sure the Open Folder radio button is selected.

---

### Post by s_g_robertson on 2009-05-08
I'm getting almost the same issue but with the places menu items trying to open in VLC.  Also when I try to go to folder properties I do not get an "open with" tab.

Any thoughts?

Thanks
Stephen

---

### Post by Dazwhite on 2009-05-08
The solution I posted above was definitely the right solution in Ubuntu 8.10. I have since upgraded to 9.04 and I see the same thing as you... no open with tab. I am assuming you are using 9.04 as well?

Sorry, I took a quick look around but couldn't figure out the solution for you.

---

### Post by 8472 on 2011-02-11
Hi,

I've run into similar problem (current gnome version: 2.32.1), and figured out that it can be fixed through similar way as Dazwhite noted previously.

Try to open "computer:///" by pressing either CTRL+L in some already nautilus opened window, or by inserting it after press Alt+F2 - and without those quotes of course.
Select the "File System" and open it's properties where select the "Open With" tab and there choose what ever you like.

---

### Post by Krytarik on 2011-02-11
> **8472 said:**
> Hi,

I've run into similar problem (current gnome version: 2.32.1), and figured out that it can be fixed through similar way as Dazwhite noted previously.

Try to open "computer:///" by pressing either CTRL+L in some already nautilus opened window, or by inserting it after press Alt+F2 - and without those quotes of course.
Select the "File System" and open it's properties where select the "Open With" tab and there choose what ever you like.
I'm wondering where you actually find the "Open With" tab on those items, since I don't have it there?

Another way, and the most accurate, would be:
Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

**EDIT:** Ahh, I got, you have to select "File System" in the folder view on the right side, not in the tree view on the left. Although I'd even prefer doing it the way *Copper Bezel* describes it below, so that not all your disks are being scanned upon doing this.

---

### Post by Copper Bezel on 2011-02-11
You don't have an "open with" tab for folders, but if you right-click any folder in Nautlius and select "open with other application," you can select Nautilus and check "Remember this application."

I used this trick in reverse to switch from Nautilus to Thunar as my default file manager. Apparently it's a common thing going around that folks have problems with this - I assume because at some point, without noticing, you did exactly the reverse and selected a folder, then "Open With" the application.

---

### Post by Krytarik on 2011-02-11
It's like described in the thread I posted, sometimes you want to open a directory with specific app, in my case with gthumb recently, and since the "Remember.." option is ticked by default, you have to untick it (in most cases). So if one time you just overlooked that, it's done. It's one of those things of OSes (I believe it's the same in Windows) I simply don't get, most of the time, if you are not alert, you would change the behaviour of your OS inadvertedly, with such an annoying outcome.

---

### Post by Krytarik on 2011-02-11
It just yet happened again. I obviously opened images one time to often  with GIMP, and whoops, it's being declared as the default action for  images. So if I just as usual double-click at an image file, it  surprisingly opens up the whole GIMP for it. Although I know of course  how to revert it, this happens over and over again. Maybe one can find a  hidden option to control that behaviour.

---

### Post by Copper Bezel on 2011-02-11
All it would take is an option to make that box unticked by default. The machine will have logged your basic preferences within a week of use. I wonder if there's a way to change the default behavior of that dialog?

Incidentally, I'm sorry I didn't see your thread - I was actually referring to a couple of threads on this accidentally getting set with music players (Exaile and Rhythmbox), almost certainly because they imported folders that way, from Nautilus.

If you right-click a file and select one of the existing "open with" items, it won't change your default preference, I don't think - it's only if you select "Open With Other Application." Once you open a file through Nautilus into a specific app, it's going to be saved onto the list of existing "open with" items. I guess I don't run into this problem, because I only ever have to hit "Open With Other Application" once per app per file type.

I mean, am I right about that? Will "Open With" (as in the listed items in the menu, without calling the dialog box) if executed enough times, change your preference without prompting? seems odd if it would.

Oh, one last oddity: I think this is actually a bug, isn't it? It makes sense that places can be associated to whatever app you choose, but someone made the commonsense assumption that no one would ever do that, so the tab isn't present in Properties. Am I misreading that? There's no logic to it working in one place but not the other.

---

### Post by Krytarik on 2011-02-11
> **Copper Bezel said:**
> 
I mean, am I right about that? Will "Open With" (as in the listed items in the menu, without calling the dialog box) if executed enough times, change your preference without prompting? seems odd if it would.
Yeah, I believe it actually did so, three times in the last weeks. I'm relatively sure. At least I didn't had that dialog, but it may be triggered by an app.

---

### Post by Alexis31 on 2011-03-20
[SIZE=4][B][COLOR=Red]The real solution for this is:[/COLOR]
[/B]
[SIZE=3][COLOR=Blue]1. Open Terminaland type:[/COLOR][/SIZE]

[/SIZE][SIZE=2][COLOR=Blue]mv ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeapps.list-old[/COLOR][/SIZE]


[CENTER][SIZE=4]**[COLOR=Red]Tadaaaa! The Places directory opens with File Manager![/COLOR]**[/SIZE]
[/CENTER]

---

### Post by Krytarik on 2011-03-20
> **Alexis31 said:**
> [SIZE=4][B][COLOR=Red]The real solution for this is:[/COLOR]
[/B]
[SIZE=3][COLOR=Blue]1. Open Terminaland type:[/COLOR][/SIZE]

[/SIZE][SIZE=2][COLOR=Blue]mv ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeapps.list-old[/COLOR][/SIZE]


[CENTER][SIZE=4]**[COLOR=Red]Tadaaaa! The Places directory opens with File Manager![/COLOR]**[/SIZE]
[/CENTER]

[SIZE=3] Yeah, if you want to kill all your other custom mimetype associations as well![/SIZE] ;-)

---

