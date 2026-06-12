---
title: "Application launcher needed"
date: 2005-12-10
forum: General Help
---

### Post by John Jason Jordan on 2005-12-10
Ubuntu-64 Breezy on Compaq laptop, upgraded from 64-bit Hoary

Like all computer users, from time to time I install new apps and remove old ones. Most of the time the installation routine does not add a launch entry into the control panel (Applications - Places - System). And when I uninstall an application the uninstall routines usually do not delete entries. And when an applications setup routines do actually add a launch line in the menu, usually they put it in the wrong folder.

I finally found that if I right-click on Applications - Places - System, and then on Edit Menus, it brings up a utility that allows me to uncheck a listing so it no longer appears in the launch listings. But still no way to add a launcher or move one around.

Oh, and Places doesn't work at all except for the Recent Documents list on the bottom. I suspect that the problem is related to the fact that I banned Nautilus from my computer one day after it ate 14 gb of my files when I was trying to back them up to another disk. But I use Konqueror now and would just as soon remove the whole Places tab.

I use just one panel, on the top. All I want is an editable drop-down list on the panel. I googled around and found what purported to be instructions for editing the applications list on the panel, but none of the screen shots looked anything like my gnome desktop.

My situation here is getting out of control. I have applications installed that I have forgotten about because I never see them in the program listing. I have others that have been removed and are still listed. Yet others I have to launch from the command line (e.g., K3B).

Is there a solution?

---

### Post by ninotob on 2005-12-10
deleted by user - accidental double post on edit

---

### Post by ninotob on 2005-12-10
[QUOTE=John Jason Jordan]
I finally found that if I right-click on Applications - Places - System, and then on Edit Menus, it brings up a utility that allows me to uncheck a listing so it no longer appears in the launch listings. But still no way to add a launcher or move one around.
[/QUOTE]

Open up that "edit menus" thing again.

At the bottom you should see some buttons:
New Menu ........ New Entry .......... New Separator
For a new program, highlight the menu you want it in, press "new entry", give it the info it needs, and voila -- joy.

Right click on an item and there appears to be a "delete" option -- grayed out though.  I imagine that it will ungray if the app is actually deleted but I haven't tested that.  You can still uncheck it even if it's stuck there.

and on the Right, two arrow keys, one points up, the other down.
Highlight an application and press one of the arrow keys.

Edit -- these options also available from the "file" menu heading in the menu editor.  Or did you want it to do something else?

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=ninotob]Open up that "edit menus" thing again.

At the bottom you should see some buttons:
New Menu ........ New Entry .......... New Separator
For a new program, highlight the menu you want it in, press "new entry", give it the info it needs, and voila -- joy.[/QUOTE]
Thanks for the suggestion, but that is not what I get. The window that pops up has three buttons on the bottom -- Help (grayed out), Defaults, and Close. No "New Menu," no "New Entry" and no "New Separator."

I suspect we are talking about different things. On my panel (I use only a top panel) the panel item is three things in one -- Applications - Places - System. If I remove it I remove all three items. Maybe there is a different Applications item that you have and which can be edited?

---

### Post by ninotob on 2005-12-10
Ok -- you want to add things to the drop down menu right -- the "start" button if you will?  

Right click in the area with the "applications, places, system" -- choose the "edit menus" option.  This is different than clicking in a blank area of the panel -- if you do that you get the option to "edit panel".  That results in a window like you just described and won't do what you want as you're well aware.  However, the "menu editor" will do what you want (if I'm understanding).

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=ninotob]Ok -- you want to add things to the drop down menu right -- the "start" button if you will?  

Right click in the area with the "applications, places, system" -- choose the "edit menus" option.  This is different than clicking in a blank area of the panel -- if you do that you get the option to "edit panel".  That results in a window like you just described and won't do what you want as you're well aware.  However, the "menu editor" will do what you want (if I'm understanding).[/QUOTE]

No, I was not clicking on a blank area of the panel. I was clicking on Aoolications - Places - System and selecting Edit Menus. The buttons you said should be at the bottom of the window are not there. I repeat, I am totally NOT clicking on a blank area of the panel.

Something is different between your Applications - Places - System and mine.

However, at the moment I am powerless to do anything about it. I installed Kdar this morning after reading here from someone who was using it to make backups. I tried to get it to make a backup to my external USB drive. It locked up Linux solid after just a few minutes. I restarted and tried again. This time it ran for about 25 minutes before locking up Linux again. And when I restarted I can no longer log in. Somehow it goobered up my user account. And you can't log in as root from the main splash screen. So basically I'm going to have to reinstall everything from scratch. That means I may lose hundreds and hundreds of hours worth of files on this computer.

I do have a backup made two days ago with Dump. But I have no idea how to do a restore.

<sigh>

---

### Post by ninotob on 2005-12-10
That's weird, because the program you described is the "add to panel" app which you get by right clicking in a blank space of the panel.  The "menu editor" option should show when you click on the "applications-Places-System" area.

Are you using Breezy?  I never tried this in Hoary and the only hoary system I have right now is running headless.

Anyway, the menu editor is mysteriously named "**smeg**", so if you open up the terminal and type "smeg", the correct application should open.  If you don't have smeg, use synaptic to install it.

---

### Post by ninotob on 2005-12-10
[QUOTE=John Jason Jordan]... I can no longer log in. Somehow it goobered up my user account. And you can't log in as root from the main splash screen. So basically I'm going to have to reinstall everything from scratch. That means I may lose hundreds and hundreds of hours worth of files on this computer.[/QUOTE]

Before you reformat and lose everything, I'm willing to bet your files are fine.  Why don't you boot up w/ a live cd (I love ubuntu but the "damn small linux" distro makes the best live cd rescue distro around), and manually copy your data to someplace else.  Then you wont have lost it.

I'm afraid I don't know anything about "dump" -- I just use tar and gzip in backup scripts to make archives which are then copied to a usb HD.  Anyway, don't give up on your data yet -- see if it's OK first.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=ninotob]Before you reformat and lose everything, I'm willing to bet your files are fine.  Why don't you boot up w/ a live cd (I love ubuntu but the "damn small linux" distro makes the best live cd rescue distro around), and manually copy your data to someplace else.  Then you wont have lost it.

I'm afraid I don't know anything about "dump" -- I just use tar and gzip in backup scripts to make archives which are then copied to a usb HD.  Anyway, don't give up on your data yet -- see if it's OK first.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)[/QUOTE]

Actually, someone else in another thread helped me get the filesystem mounted using the Ubuntu Live CD. All my stuff is there. I also got the networking going with the Live CD and copied everything to my Windows computer. So the data is safe. Now all I will lose is a zillion settings. All the custom stuff in OpenOffice.org (years of adding terms to the user dictionary), and so on.

Another interesting thing I just discovered (getting back to the subject of this thread) -- the Edit Menu on the Live CD has the extra buttons on the bottom. But when I did the exact same thing on my [currently sort of defunct] system the buttons were not there.

But now that I know the applet is 'smeg' I will try that, assuming I can get things back.

Oh, and one other thing. It just occurred to me that the problem with Edit Menu may be because I uninstalled Nautilus. I did that after it ate 14 Gb of mp3s one day. I now use Konqueror. Nautilus is banned from my computer.

---

### Post by ninotob on 2005-12-10
[QUOTE=John Jason Jordan]
Oh, and one other thing. It just occurred to me that the problem with Edit Menu may be because I uninstalled Nautilus. I did that after it ate 14 Gb of mp3s one day. I now use Konqueror. Nautilus is banned from my computer.[/QUOTE]

Wow!  I've been a KDE user for many years but I thought I'd give gnome a go for a while -- it's way better than it used to be and I'm liking it thus far.  In your case, if you are going to use Konqueror, why not just go completely KDE?  That way you'll have consistent desktop environment.

As an asside, I think you'll find your openoffice dictionaries in a hidden folder ".openoffice" located in your home directory -- just keep drilling down, you'll see the stuff.

EDIT -- how did nautilus eat the 14gb?  I worry because in the past when I've tried earlier versions of gnome, it seemed pretty unstable compared to KDE -- I'm really liking the current version but comments like this worry me.

---

### Post by John Jason Jordan on 2005-12-11
[QUOTE=ninotob]EDIT -- how did nautilus eat the 14gb?  I worry because in the past when I've tried earlier versions of gnome, it seemed pretty unstable compared to KDE -- I'm really liking the current version but comments like this worry me.[/QUOTE]
Here is a copy and paste from a writeup I made right after it happened:

---
I've HAD it!!!!

I just lost about 14 Gb of files. Permanently gone. This happened
while trying to burn them to a DVD for backup. Yes, there is no
backup.

Originally I selected the whole folder (about 20 Gb.). But Nautilus
does not tell you how many bytes the folder is unless you select all
the files. Not knowing how many there were, I dragged them all to a
burn window. When I tried to burn a DVD it did not tell me that there
were too many files to fit. No, the stupid thing said there was no DVD
in the drive. What it was trying to tell me was that there was not a
DVD capable of holding 20 Gb in the drive. But the only error message
it knows is "No disk in drive."

So after removing and replacing the blank DVD various times I 
decided to use a CDR instead, and this time I knew it couldn't hold
all the files, so I selected just 600 Mb of them in the burn window.
But once again, I got the error message. Turns out that whatever is in
the burn window is what it wants to burn. Never mind that you have
selected only some of them.

OK, have to remove the others from the burn window. But from past
experience, this is very dangerous. You see, it did not occur to the
Nautilus programmers that it would be useful to show different icons
for file vs. shortcut to file. In other words, there is no way to tell
whether you are deleting the file, or a shortcut to it. 

After thinking about this for a bit I decided I'd drag the extra files
back to the original folder. This, I reasoned, would generate an error
message if what was in the burn window was really a copy of the file
instead of just a shortcut to it.

And it did, indeed, generate the error message. Fine. "I'll just
cancel this operation then," I thought. Except the programmers forgot
to put a cancel button on the error message box. So I tried hitting
the X in the corner of the box, but it was grayed out. So were the Xs
in the windows for the burn window and the original folder window. And
the only buttons on the error message window were Skip, Overwrite, and
Overwrite All. So I clicked on Skip. And it skipped the file. But
there were 301 files. Looked like I'd have to click on Skip 301 times.
They also forgot to put in a button for "Skip All." So I decided, "if
these are just copies of the files, let it go ahead and overwrite them
-- won't make any difference." So I clicked on Overwrite All. And
guess what effing Nautilus proceeded to do? It overwrote 301 files
with NADA. They all disappeared. They're not in the Trash, they are
nowhere. Gone. Just plain gone. 

This is a Very Bad Bug. 

I have to manipulate files constantly on this computer and the 
command line is just too time consuming. Seldom do I need to 
move files with something in common so I can use wildcards. 
Usually I want just "this file" and "that file" and "that other file"
and so on. Too much typing to do it from the command line. I really
depend on a GUI file browser.

Tonight's exercise has be so furious that if I can't get a decent file
browser that actually works reliably and has a user interface that has
actually been thought out, I swear I'm gonna unsubscribe, wipe out
Linux, and install Windows 2000. I just lost four days work. I've HAD
IT.

And save the pontificating. "You should have been making backups as
you went along" is not going to make me feel any better about an OS
whose users think it's OK to have a file browser that crashes several
times a day and destroys files.
-----

So that's the story. I love Ubuntu. I love gnome. But Nautilus will never be on a computer of mine.

---

