---
title: "Changing default apps"
date: 2005-12-13
forum: General Help
---

### Post by remick182 on 2005-12-13
How do I change some of the system default applications in Ubuntu, such as making xine my default app to play dvd's instead of totem?

---

### Post by SickTwist on 2005-12-13
[QUOTE=remick182]How do I change some of the system default applications in Ubuntu, such as making xine my default app to play dvd's instead of totem?[/QUOTE]

To change the default program that opens DVDs, select "System"-->"Preferences"-->"Removable Drives and Media". Click the "Multimedia" tab and change the command for Video DVD Discs to "gxine /dev/dvd" without quotes and and change /dev/dvd to the appropriate device file if it is something else.

-or-

You could make totem use xine to render the video. (It will play the same as gxine but the interface will look like totem.) Do this by running the following command (it will ask to remove totem-gstreamer, that is OK):

sudo apt-get install totem-xine

If you wish to change the default application for a specific file type (plain text, html, open document, svg, jpg, etc.), right-click on a file of that type in nautilus and click "Properties". Then click the "Open With" tab and click the "Add" button to add program to the list of applications that can open that file. After you have added one or more programs to the list, click on the radio button next to the name of the program that you would like to set as the default. Click "Close" and you're done.

---

### Post by ubunny on 2005-12-13
I use VLC media player instead of Totem which seems to have no particular purpose only to tell me that it can't play anything.

Thanks for the notes above.  Normally everytime I have an .avi file or dvd to play, totem tries to load.  Everytime I select VLC media player as the radio button selection for these file formats, but ubuntu does not remember this on reboot.  System -- preferences -- Removable Drive and Media -- Multimedia really did the trick, removed totem %d and replaced with vlc %d.

However totem can't be removed??

```
 sudo apt-get remove totem
Reading package lists... Done
Building dependency tree... Done
Package totem is not installed, so not removed

```

arr....totem still lives!  Don't believe me?

```
 whereis totem
totem: /usr/bin/totem /usr/lib/totem /usr/bin/X11/totem /usr/share/totem /usr/share/man/man1/totem.1.gz

```

at this point totem must die.  How do I kill it?  apt-get remove didn't do it.

thanks
u

---

### Post by kaamos on 2005-12-13
the name of the package is either totem-xine or totem-gstreamer. Try removing the one you have.

To see what you have installed, use the command: dpkg -l | grep totem
Or just use synaptic.

---

### Post by ubunny on 2005-12-13
thanks.  that worked and totem is dust.  I could use synaptic but especially like the command line tools, so appreciate the dpkg information.

cheers
u

---

### Post by remick182 on 2005-12-13
[QUOTE=SickTwist]To change the default program that opens DVDs, select "System"-->"Preferences"-->"Removable Drives and Media". Click the "Multimedia" tab and change the command for Video DVD Discs to "gxine /dev/dvd" without quotes and and change /dev/dvd to the appropriate device file if it is something else.

-or-

You could make totem use xine to render the video. (It will play the same as gxine but the interface will look like totem.) Do this by running the following command (it will ask to remove totem-gstreamer, that is OK):

sudo apt-get install totem-xine

If you wish to change the default application for a specific file type (plain text, html, open document, svg, jpg, etc.), right-click on a file of that type in nautilus and click "Properties". Then click the "Open With" tab and click the "Add" button to add program to the list of applications that can open that file. After you have added one or more programs to the list, click on the radio button next to the name of the program that you would like to set as the default. Click "Close" and you're done.[/QUOTE]

OK.  I made the changes through the [COLOR="RoyalBlue"]"System"-->"Preferences"-->"Removable Drives and Media"[/COLOR] tabs and that worked fine, however, Xine gives an error when trying to autoload the DVD.  I get:
[COLOR="SeaGreen"]- xine engine error -
There is no demuxer plugin available to handle '/dev/hdd'.  Usually this means that the file format was not recognized.[/COLOR]
When I hit the DONE button, I can click the DVD tab on the GUI and it loads right up.  Why am I getting this initial error?

---

### Post by SickTwist on 2005-12-14
I took a look at the man page for gxine and it appears that this is the format for starting gxine with a DVD:

gxine dvd:/

Try that and see if it works.

---

### Post by anil_robo on 2005-12-14
[quote=ubunny]thanks.  that worked and totem is dust.[/quote]

Totem is perhaps the most hated app in the entire Ubuntu OS!

---

### Post by John Jason Jordan on 2005-12-14
I have tried everything, but nothing works. I currently have Totem (totem-xine), Gxine, Mplayer and VLC installed on my 64-bit Breezy. Here is what happens:

Totem: Opens and immediately closes. (Same thing happened before when I had the default version.) Doesn't matter if a video DVD is in the drive or not. It displays a message, but disappears too fast to read it.

Gxine: I just now installed it, but the results are the same as for Totem above.

MPlayer: Stays open, but can't seem to play anything. Part of the problem is that I can't figure out what button does what. The top button on the round thing in the middle opens a browser window. It sees the DVD in the drive (right now "I Robot" is in the drive), and it says /media/cdrom0/VIDEO_TS, which I think is one of the files on the DVD. But when I click on OK it moves to my home folder instead of opening the file. The control panel window says "no media opened." Very strange.

VLC: Stays open, but when I click on Video it says "empty." Can't figure out how to point it to the DVD drive.

Also tried various things in the System > Preferences > Removable Drives and Media, but nothing makes anything open automatically when a movie DVD is placed in the drive. Originally it said "totem %d" and Totem automatically started when a DVD was placed in the drive (but immediately closed). Then I uninstalled Totem. Now I have installed totem-xine, but "totem %d" or "totem-xine %d" doesn't make it launch automatically.

---

### Post by Perfect Storm on 2005-12-14
Check this little howto I made. [http://ubuntuforums.org/showthread.php?t=77146](http://ubuntuforums.org/showthread.php?t=77146)

---

### Post by remick182 on 2005-12-14
[QUOTE=SickTwist]I took a look at the man page for gxine and it appears that this is the format for starting gxine with a DVD:

gxine dvd:/

Try that and see if it works.[/QUOTE]

I read through AI's Howto and did some tweaking.  I got everything working after some trial and error by inputting this into the Video DVD Discs field:
**[COLOR="Blue"]xine dvd:///dev/dvd[/COLOR]**
Now it works great!  Thanks for all of your assistance.  Oh, and I was wondering if anyone knows what the **[COLOR="DarkOrange"]%d[/COLOR]** means when used in the terminal after a command, or in Linux in general.  That was what caused the error, but I'm also seeing it pop up in an error I've been getting every once in a while when trying to burn DVD's with xDVDShrink and lxdvdrip.

---

### Post by John Jason Jordan on 2005-12-15
[QUOTE=remick182]I read through AI's Howto and did some tweaking.  I got everything working after some trial and error by inputting this into the Video DVD Discs field:
**[COLOR="Blue"]xine dvd:///dev/dvd[/COLOR]**
Now it works great!  Thanks for all of your assistance.  Oh, and I was wondering if anyone knows what the **[COLOR="DarkOrange"]%d[/COLOR]** means when used in the terminal after a command, or in Linux in general.  That was what caused the error, but I'm also seeing it pop up in an error I've been getting every once in a while when trying to burn DVD's with xDVDShrink and lxdvdrip.[/QUOTE]
I finally got Gxine to open and stay open. It even sees the DVD in the drive now. Totem, VLC and MPlayer still don't work, but as long as one of them works, that's good enough. Gxine doesn't pop up when I put a DVD in the drive, in spite of the fact that the box to do so is checked. But I don't really care about that.

However, now I have a related problem. I put a DVD ("I Robot") into the drive and Gxine says "Encrypted media stream detected Media stream scrambled/encrypted." This also happens with all other movies I try to play. So now what? Am I missing some crucial parts here that are necessary to descramble/deencrypt the DVD?

---

### Post by tanis143 on 2005-12-15
Ok, but how would I change which app a .mp3 is played with? I like xmms much better than totem, but I can not get it to open with xmms instead.

---

### Post by SickTwist on 2005-12-16
[QUOTE=tanis143]Ok, but how would I change which app a .mp3 is played with? I like xmms much better than totem, but I can not get it to open with xmms instead.[/QUOTE]

[QUOTE=SickTwist] . . . If you wish to change the default application for a specific file type (plain text, html, open document, svg, jpg, etc.), right-click on a file of that type in nautilus and click "Properties". Then click the "Open With" tab and click the "Add" button to add program to the list of applications that can open that file. After you have added one or more programs to the list, click on the radio button next to the name of the program that you would like to set as the default. Click "Close" and you're done.[/QUOTE]

Let us know if you need more details.

---

