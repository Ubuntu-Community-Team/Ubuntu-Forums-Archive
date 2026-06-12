---
title: "Mythbuntu Issues"
date: 2009-02-01
forum: General Help
---

### Post by el_heffe on 2009-02-01
I have the Mythbuntu working, wonderfully.  But there are a few issues that are outstanding and the Mrs. is getting perturbed.  A bit of a background first:
It is a Core2Duo Allendale with an nVidia video card of some sort being used for output to the tv.  I have two Happauge 150's and IIRC 2g of ram and a 300g HD.  There is a streamzap remote being used, and it is connected via ethernet.  I have installed all the updates as they come in.

Like I said- its about 90%.  It records programs I have setup, it plays audio, I can turn the volume up and down, change channels, PiP, and so on and so forth.  My issues remaining are:

-there are unused buttons on my Streamzap.  I would like to use them and have NO clue what to do in this regard.  The colored buttons on the bottom, the power button, the FFWD RWND buttons and possibly more.

-It seems slow, this isnt some crappy old p3 350 with some video cards and a bunch of ram.  changing channels takes a second or two- is this normal?  if it is normal, i can deal- like digital cable. 

-i have it set to 1 simultaneous job, should it be more because of the second video card?

-is the second video card being used to help record? what is a good way to check that out?

-it freezes once in a while, is this also normal?

I am *very* happy with Mythbuntu, ubuntu in general rocks, but I digress.  **** works, babys mama is excited because now she doesnt have to watch Gray's Anatomy on the computer and can skip commercials but there are some small issues to iron out.  Iron out those issues shes happy, I am happy.  Any help is appreciated.

---

### Post by txcrackers on 2009-02-01
- The remote control buttons are handled through lirc. There's a lircrc file in the $HOME/.mythtv directory that's being used. You'll want to make a backup of the working file before dorking around with it.

- The hesitation in changing channels is that Myth is buffering the input to start saving to disk. Normal behavior.

- The "jobs" are background processes like commercial flagging and transcoding. If you do a lot of recording, you can try setting this higher, but with more jobs, you could bog down the system. YMMV.

- The second card will be indicated in just about any view of upcoming recordings. I've found it easier to see it in the Mythweb interface.

- It depends. If its something involving switching video streams, probably. There's a lot of potentically heavy graphics stuff going on here and some (relatively) time-intensive stuff may just take a bit of time...

---

### Post by el_heffe on 2009-02-02
Thanks for the help, I will pass on the relevant info to my better half, and check out the other things you mention.  With an luck I will get that darn remote working, AND have her be more happy about this.  She is a little perturbed right now, but thats possibly because it is different than what she is used too.  I do have another question though, on something that happened last night.

- with PiP on I wanted to swap them out.  This worked just fine, but I was unable to switch back nor was I able to select PiP again.  Was this because I was recording one show that was the original big screen or because the system borked?  Thanks for any more of our great help!

---

### Post by &lt;mike&gt; on 2009-11-26
> **txcrackers said:**
> - The remote control buttons are handled through lirc. There's a lircrc file in the $HOME/.mythtv directory that's being used. You'll want to make a backup of the working file before dorking around with it.


My lirc config file is located in $HOME/.lirc
There are several files in that directory; the one called mythtv controls mythtv; the one called vlc programs the buttons for the vlc media player, and so on.

lirc basically treats your infrared remote control as a sort of a keyboard. There's a config file in /etc/lirc (or referred to in there) which converts infrared signals into readable names, like KEY_MENU or KEY_PLAY. The config files in ~/.lirc/ then convert these names into key presses like 'M' or 'P'. 

My config files were created by the mythbuntu control centre, but when you have something as a base they're really quite easy to add to.

The files are in the form of

```
begin
    remote = <remote name>
    prog = mythtv
    button = <remote button name>
    config = <key to map to>
    repeat = <number of additional times to press the key>
    delay = <delay before pressing>
end
```

For example (this copied straight out of my config)
```
begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_BACKSPACE
    config = Escape
    repeat = 0
    delay = 0
end
begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end
```

To determine the remote button name, open a terminal and type
```
 irw 
```
then press buttons on the remote and you should see the names appear.

Probably the easiest way to determine the keys to map to (these are the same keys you would use if you actually had a keyboard plugged into the computer) is to fire up mythweb and go to settings/mythtv/keybindings. There are two bits to look for here: the jump points and, in the second table, look for 'Global' and 'TV Frontend'. Live TV, for example is Shift Control T. In the lirc keymap, this would be 'shift-ctrl-T'. Menu is just 'M'.

> **el_heffe said:**
> 
-is the second video card being used to help record? what is a good way to check that out?

If you can watch live tv while recording, record two programs at once, or have the picture in picture option in the menu when you press 'M' while watching live TV, then the second card is working. If you go to manage recordings / upcoming recordings in Mythfrontend, you will see the card number on the right hand side (along with C=conflict, P=previously recorded, R=recording, N=not found, etc.). Schedule two programs at once and go to upcoming recordings; if you see different numbers, then both tuners are being used.

> **el_heffe said:**
> 
-it freezes once in a while, is this also normal?

Mine doesn't freeze. You might want to see if there are other symptoms occurring at the same time... e.g., check
```
 tail -n 25 /var/log/syslog 
```
or
```
 dmesg 
```
and if there are, then either post back here or search for an existing thread with your particular error message.

---

