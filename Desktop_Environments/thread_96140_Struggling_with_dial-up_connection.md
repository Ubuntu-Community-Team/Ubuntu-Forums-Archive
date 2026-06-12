---
title: "Struggling with dial-up connection"
date: 2005-11-28
forum: Desktop Environments
---

### Post by L Campbell on 2005-11-28
I have Ubuntu 5.10 and it doesn't seem to be able to see my SmartLink dial-up modem.

[www.linmodems.org](www.linmodems.org)  seems to have some helpful instructions, so I downloaded their  scanModem.gz  file to a floppy.

Their instructions say to use  mcopy a:scanModem.gz.  to copy it into my account.

When I try this, I get  bash: mcopy:  command not found

I would appreciate it if someone would give me some advice here.

Thanks.

Lewis.

*********

---

### Post by kalin on 2005-11-28
Just browse the floppy contents (should be in the Places menu, if not - look in Places->Computer) and copy it from there into your Home folder.

---

### Post by L Campbell on 2005-11-28
[QUOTE=kalin]Just browse the floppy contents (should be in the Places menu, if not - look in Places->Computer) and copy it from there into your Home folder.[/QUOTE]


Thanks for your suggestion.

I tried this and got ' unable to mount the selected volume ' when I tried to contact the floppy.

Is there something else that I can try?

Thanks.

Lewis.

********

---

### Post by kalin on 2005-11-28
Try typing

```
dmesg | tail
```

in a terminal, right after you try to access the floppy drive, and tell us what's the output, that would show more detailed error messages.

---

### Post by L Campbell on 2005-11-28
[QUOTE=kalin]Try typing

```
dmesg | tail
```

in a terminal, right after you try to access the floppy drive, and tell us what's the output, that would show more detailed error messages.[/QUOTE]
................................

I appreciate your continued help here.

I opened a terminal and typed in your suggestion.  Not knowing how to create the verticle line, I took a chance and thought that perhaps you were emphasizing a 'space'.

BTW, I did notice the floppy drive light come on momentarily during the boot process.

Next I went to Places > Computer and clicked on the floppy.  The result was the same as previously, so I then entered the code that I had typed into the 'terminal'.

All I got was a mountain of lines, similar to this:-

    [4294759 . 77400]   IPv6 over IPv4 Tunneling driver

Kind regards.

Lewis.

********

---

### Post by GeneralZod on 2005-11-28
[QUOTE=L Campbell]
I opened a terminal and typed in your suggestion.  Not knowing how to create the verticle line, I took a chance and thought that perhaps you were emphasizing a 'space'.
[/QUOTE]

Hi Lewis,

In UNIX-y parlance, the vertical line is called the "pipe" symbol, and is a way of re-directing the output from one command (in this instance, the "mountain of lines" you described) into another command, in this case "tail".  "tail" is a very simple command that takes the mountain of lines and simply outputs the last 10 of them - type

```

man tail

```

for more details!

"dmesg" is the command for listing a huge load of kernel output, which will likely include, amongst other things, reasonably descriptive explanations of what went wrong when you tried to mount the floppy disc.  Thus typing 

```

dmesg | tail

```

will return the last 10 things that the kernel complained about which, if you did it soon enough after trying to mount your floppy disc, will hopefully contain some  information relevant to the task at hand.

Just thought I'd indulge in one of those "The More You Know!(TM)" moments ;)

---

### Post by kalin on 2005-11-28
It seems you have a problem with the floppy (the media for example), it should not be a problem to mount a regular FAT-formatted floppy in Ubuntu. The "dmesg" command dumps all kinds of information from the kernel, the "| tail" part simply cuts it's output just to the last few lines, hopefully those related to the failed mounting.

There should be a "|" key somewhere on you keyboard, usually somewhere around the Enter key, I believe I've also seen it on some keyboards near the left "Shift" button, try finding it, it will be useful in the future :)

Additionally could you try opening the diskette somewhere else just to see if it's fine?

Edit: heh GeneralZod beat me to the "| tail" explanation

---

### Post by L Campbell on 2005-11-28
Well, Gentlemen, I have finally taken a step forward.   :-)

I won't tell you how long it took me to find the 'pipe' symbol but I will 'fess up that I had to call my girlfriend.

It looks like I'm out of time today but I _DO_ have 10 lines of code and hope to have figured out how extricate them from the Ubuntu section of my dual boot machine and be able to post them here, with the Win 98 side of the machine, by tomorrow.

Many thanks again.

Lewis.

*********

---

### Post by L Campbell on 2005-11-29
[QUOTE=L Campbell]Well, Gentlemen, I have finally taken a step forward.   :-)

I won't tell you how long it took me to find the 'pipe' symbol but I will 'fess up that I had to call my girlfriend.

It looks like I'm out of time today but I _DO_ have 10 lines of code and hope to have figured out how extricate them from the Ubuntu section of my dual boot machine and be able to post them here, with the Win 98 side of the machine, by tomorrow.

Many thanks again.

Lewis.

*********[/QUOTE]

Again I made some progress, then hit another road block.

Ubuntu recognized my floppy drive, sufficiently to format a floppy disk but when I tried to copy my ' 10 lines of code ' file to it I got the message  
' unable to mount the selected volume '.

I guess I'll have to read and type out the '10 lines of code', this way you gentlmen will be able to see whats going on?

Kind regards.

Lewis.

****************

---

### Post by StuartZ on 2005-11-29
I have been having problems to and found this:

[http://lists.ubuntu.com/archives/ubuntu-users/2005-November/057130.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-November/057130.html)

---

### Post by L Campbell on 2005-11-30
[QUOTE=kalin]Try typing

```
dmesg | tail
```

in a terminal, right after you try to access the floppy drive, and tell us what's the output, that would show more detailed error messages.[/QUOTE]

Here is the code:-

[4294745.222000] B1uetooth: HCI device and connection manager initialized
[4294745.222000] B1uetooth: HCI socket layer initialized
[4294745.312000] B1uetooth: L2CAP ver 2.7
[4294745.312000] B1uetooth: L2CAP socket layer intitialized
[4294745.372000] B1uetooth: RFCOMM ver 1.5
[4294745.372000] B1uetooth: RFCOMM socket layer intitialized
[4294745.372000] B1uetooth: RFCOMM TTY layer initialized
[4294755.338000] NET: Registered protocol family 10
[4294755.339000] Disabled Privacy Extensions on device c02eb280(1o)
[4294755.339000] IPv6 over IPv4 tunneling driver

Hopefully this will enable you to see what went wrong.

Kind regards.

Lewis.

**********

---

### Post by L Campbell on 2005-11-30
[QUOTE=kalin]Try typing

```
dmesg | tail
```

in a terminal, right after you try to access the floppy drive, and tell us what's the output, that would show more detailed error messages.[/QUOTE]

Here is the code:-

[4294745.222000] B1uetooth: HCI device and connection manager initialized
[4294745.222000] B1uetooth: HCI socket layer initialized
[4294745.312000] B1uetooth: L2CAP ver 2.7
[4294745.312000] B1uetooth: L2CAP socket layer intitialized
[4294745.372000] B1uetooth: RFCOMM ver 1.5
[4294745.372000] B1uetooth: RFCOMM socket layer intitialized
[4294745.372000] B1uetooth: RFCOMM TTY layer initialized
[4294755.338000] NET: Registered protocol family 10
[4294755.339000] Disabled Privacy Extensions on device c02eb280(1o)
[4294755.339000] IPv6 over IPv4 tunneling driver

Hopefully this will enable you to see what went wrong.

Kind regards.

Lewis.

********

---

### Post by kalin on 2005-11-30
Hi again, the messages don't have anything helpful, but following StuartZ's advise I've looked around, and it seems it's a common problem, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=85777&highlight=floppy](http://ubuntuforums.org/showthread.php?t=85777&highlight=floppy)

You should be able to mount the floppy using the terminal, then after you have setup your modem the best thing would be to update the system and the problem is supposed to go away.

Let us know how it turns out.

---

### Post by L Campbell on 2005-11-30
[QUOTE=kalin]Hi again, the messages don't have anything helpful, but following StuartZ's advise I've looked around, and it seems it's a common problem, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=85777&highlight=floppy](http://ubuntuforums.org/showthread.php?t=85777&highlight=floppy)

You should be able to mount the floppy using the terminal, then after you have setup your modem the best thing would be to update the system and the problem is supposed to go away.

Let us know how it turns out.[/QUOTE]

Thanks for taking the time to check on me.   :-)

That looks like a good thread and I have copied it.

Here is my latest 'status' report.

...............
I now have  scanModem.gz  on both a floppy and a CD but have been unable to copy  it into my ‘home folder’.


When I boot up, the light on my floppy drive flashes on and I have been able to format a floppy  disk.  However, when I insert a disk into the floppy drive and try to open it, all I get is the message, ‘ERROR: given UDI is not a mountable volume’.

If I try to copy the file from the CD, it is not visible and a ‘file search’ indicates that I don’t have any such file.
....................

Kind regards.

Lewis.

*******

---

