---
title: "changing default cd player"
date: 2005-03-01
forum: Desktop Environments
---

### Post by rabadash on 2005-03-01
I want to make xmms my default cd player  I know it's under Computer>Desktop Preferences>Removable media.  For command I just typed xmms, which starts xmms when I insert a cd, but it doesn't start playing and I have to browse to find the cd.  Problem is that I don't know how to get xmms to start and begin playing automatically.

---

### Post by doitashimashite on 2005-03-02
You can define whatever application you want to use in

Computer
Desktop Preferences
Removable Storage
Audio CD's

---

### Post by KrIaXPaTaLa on 2005-03-26
Thats helpfull...

---

### Post by RainyDay on 2005-03-27
I too have this problem. I want xmms to autoplay CD's when one
is inserted into the drive. As I don't have analogue CD cables
fitted I need the digital extraction facilities of xmms. I can do this
manually so xmms is set up ok, I just can't figure out how to make
it happen automatically.

Although the advice below is helpful:

>Computer
>Desktop Preferences
>Removable Storage
>Audio CD's

could someone tell me what to replace the following string with:

>gnome-cd --unique --play --device %d

I have tried:

/usr/bin/xmms cdrom://

this almost works, in that it starts xmms and opens the filer window.
However no files are loaded. I suspect that a variable of some sort
should be placed at the end of the line above.

Thanks in advance

.....RainyDay

---

### Post by steffen on 2005-04-23
[QUOTE=RainyDay]I too have this problem. I want xmms to autoplay CD's when one
is inserted into the drive. As I don't have analogue CD cables
fitted I need the digital extraction facilities of xmms. I can do this
manually so xmms is set up ok, I just can't figure out how to make
it happen automatically.

Although the advice below is helpful:

>Computer
>Desktop Preferences
>Removable Storage
>Audio CD's

could someone tell me what to replace the following string with:

>gnome-cd --unique --play --device %d

I have tried:

/usr/bin/xmms cdrom://

this almost works, in that it starts xmms and opens the filer window.
However no files are loaded. I suspect that a variable of some sort
should be placed at the end of the line above.

Thanks in advance

.....RainyDay[/QUOTE]

Wondering about this as well.

---

### Post by glennric on 2006-06-24
I just figured this out.  Use the following for the Audio CD Discs command in System->Preferences->Removable Drives and Media->Multimedia:

```
/usr/bin/xmms --play --queue /media/cdrom
```

This worked for me at least.

---

### Post by bricedebrignaisplage on 2006-07-21
perfect :D 
Thanks

---

### Post by LinuxLemur on 2006-07-23
> **glennric said:**
> I just figured this out.  Use the following for the Audio CD Discs command in System->Preferences->Removable Drives and Media->Multimedia:

```
/usr/bin/xmms --play --queue /media/cdrom
```

This worked for me at least.

It worked.  Yesterday at least.  Today I am having problems playing any CD's at all. It autoplays the track, but no sound.  I will figure the problem out I am sure, but until then, I would like to put Sound Juicer back as the default CD player.  The problem is that the "Removable Drives and Media Preference" does not save the orignal Sound Juicer command line (with the switches) in the drop down.  Kind of defeats the purpose of the dropdown.  You know where I can find it?

---

### Post by LinuxLemur on 2006-07-23
Well, I found it on my other computer:

sound-juicer -d %d

Then I added to the end:

 --play --queue /media/cdrom

Thanks for the thread.

---

### Post by darknuala on 2006-07-30
So what if I want to change the default player for mp3 or ogg files?

---

### Post by LinuxLemur on 2006-08-05
Just in case you didn't figure it out, you right click on the media file (any mp3 file for example) and goto properties.  Select the "open with" tab and select XMMS.

---

### Post by cjazinski on 2006-08-09
That works for clicking each mp3, but lets say i want to setup a keyboard shortcut to open the default media playing app. which is rythumbox at the moment, is there anyway to change that to xmms? reason for it, is i have front panel buttons on my E1505 dell laptop and i would like to use those buttons. Thanks

---

### Post by klytu on 2006-08-19
> **glennric said:**
> I just figured this out.  Use the following for the Audio CD Discs command in System->Preferences->Removable Drives and Media->Multimedia:

```
/usr/bin/xmms --play --queue /media/cdrom
```

This worked for me at least.

With muliple CD/DVD drives, this worked for me:

```
/usr/bin/xmms --play --queue %d
```

or also just:
```

xmms --play --queue %d

```

---

### Post by ecethan on 2006-08-21
to fix the No Audio on from CD do this 
Switch the default player to XMMS  VIA 
System > Pref > Removeable Drives and Media > Multimedia Tab 
```
/usr/bin/xmms --play --queue /media/cdrom
```

if then you do not have Audio from your cd In XMMS do this 
XMMS > Options > Pref > Configure CD Audio Player 
Change Play mode From Analog to Digital Audio Extraction then apply. 
it should all be fixed :)

---

### Post by TKR101010 on 2007-08-09
I realize that this is an old post, but it doesn't look like anyone responded to darknuala's question.

If you right-click on a file, and go to the 'Open with' tab, you can change the default program for that file type (of the file you right-clicked)

Now the next person searching for that answer won't find a dead-end thread. :)

---

