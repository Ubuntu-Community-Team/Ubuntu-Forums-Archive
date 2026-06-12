---
title: "Lucid: gltext.desktop changes have no effect?"
date: 2010-05-20
forum: Desktop Environments
---

### Post by edgue on 2010-05-20
I am "forced" to use the "gnome screen saver" (seems like our company internal chat client only recognizes me as "away" when the gnome screen saver is running). Anyway ...

with karmic, I manually changed the content of

/usr/share/applications/screensavers/gltext.desktop

to display a digital clock as screensaver (modify the Exec line to 
provide different arguments to gltext)

I applied the same change on Lucid ... but gltext keeps displaying 
machine name + kernel name?!

any idea what could be causing this?

---

### Post by ZepoL~ on 2010-06-08
Hi, try chmod 444 to the gltext.desktop file.  I just did that, and it worked.  Hope it helps you!

---

### Post by edgue on 2010-06-09
> **ZepoL~ said:**
> Hi, try chmod 444 to the gltext.desktop file.  I just did that, and it worked.  Hope it helps you!

Thanks for the hint; but that didnt help. 

Well, at least for what I tried: I reset the file permissions; changed the file content and had a look into the screensaver preview ... and that did still show what I specified BEFORE making these changes.

Luckily its right now showing what I want to see ... I changed the file some time ago; then screensaver got an update ... and I guess that somehow caused that the screensaver is now showing what i specified in the file. But I have NO idea how to change the "displayed" stuff in a deterministic way.

---

### Post by ZepoL~ on 2010-06-09
Well, just like you I had it working until I upgraded from 9.10 to 10.04.  After the upgrade it just showed the kernel info for gltext.  

After trying several things I just changed it to 777, and the preview showed what I wanted.  So after that I changed it to 444 because I didn't want it to be 777, and it still stayed the same, so I decided to post my results for you.  I'm sorry 444 didn't work.  Can you try 777 and see if that works?  If so then you can change it to 444.  I hope that works for you.

---

### Post by edgue on 2010-06-10
I tried this:

- change the file content to differ from what is currently used
- change the permissions to 777
- open the System->preferences->Screen saver ...

volia ... the "preview" ... still shows me the "original" content

wtf?!

---

### Post by dominiquec on 2010-06-27
Tried the permissions change, but no effect for me, either. :-(

This is annoying.

---

### Post by Totbuae on 2010-06-29
After spending the better part of a day searching I think I found an answer.

Post #7 from Wolki on this thread explains how to do it.
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=364765[/COLOR]]("http://ubuntuforums.org/showthread.php?t=364765")

Just in case the above isn't 100% clear, here it is in different words.

Make a copy of /usr/share/applications/screensavers/gltext.desktop in your home directory to work on it.

```
sudo cp /usr/share/applications/screensavers/gltext.desktop ~/glyourtext.desktop
```

Change ownership of the file (this step might not be necessary).

```
sudo chown you:yourgroup glyourtext.desktop
```

Fire up gedit and proceed to make the usual changes to the Exec line.  Change the Name line if you want a new entry in the screensavers list or leave it as GLText if you want to replace the default GLText.

```
gedit glyourtext.desktop
```

```
[Desktop Entry]
Name=[COLOR="Red"]GLYourText[/COLOR]
Exec=/usr/lib/xscreensaver/gltext -root [COLOR="Red"]-front -text "Your text."[/COLOR]
TryExec=/usr/lib/xscreensaver/gltext
Comment=GLText with custom message.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
OnlyShowIn=GNOME;
```

Save the file and close the editor.

Open a Nautilus window (the gnome file browser, Places > Home Folder) and a screensaver preferences window (System > Preferences > Screensaver).

Find the .desktop file you just saved (glyourtext.desktop) in the Nautilus window and drag-n-drop it on the screensaver preferences window.

Close and reopen the screensaver preferences window and you should see a GLYourText entry in the list of screensavers which should show your custom text.

If you happen to drag-n-drop the .desktop file several times, your list will end up with multiple GLYourText entries.  To get rid of the extra ones go to ~/.local/share/applications/screensavers/ and delete the duplicate files (finding this out is what took most of my "research" time XD ).

I haven't tested if copying gltext.desktop directly to ~/.local/share/applications/screensavers/ and editing it there would obviate the drag-n-drop from Nautilus to the screensaver preferences step.

---

### Post by ZepoL~ on 2010-06-29
Sorry, I'm new at this, I guess I should have posted what was in my gltext.desktop file.  Thanks Totbuae for posting additional information.  I was the owner of the new file when I changed the permissions.  I had renamed the file to .old then created a new one and pasted the info in, edited it, and then changed the permissions.  I'll make sure to be more thorough.  My apologies everyone.

---

