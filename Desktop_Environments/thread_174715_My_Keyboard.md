---
title: "My Keyboard"
date: 2006-05-12
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-12
I have one of those fancy keyboards. Its a Dynex with those extra buttons. I want to get Amarok to let it use the "Play", "Stop", etc buttons as shortcuts, but it doesn't read a key press when I do so. Any suggestions? I'm at school right now, so I'm going to get a model number later.

---

### Post by vidak on 2006-05-13
You should have the packages hotkey-setup and hotkeys installed. 
Start a console, and run xev. (the xev window should be the active one)
Press the extra buttons, and write down the keycodes. (like 264)
If you are lucky, there is a config file for your keyboard in hotkeys - they are located in /usr/share/hotkeys, I think. (it has a very good manual btw)
Start hotkeys: hotkeys -t mykeyboardtype
Try to use your hotkeys, if something won't work, copy a config file from /usr/share/hotkeys/ to .hotkeys/ and edit it. It's a good idea to have a copy of /etc/hotkeys.conf in .hotkeys/ (and editing it, too).
The structure of these config files are quite easy to understand...

Tell us, whether this solution helps or not...

---

### Post by Wr8EYilK8Y on 2006-05-15
Okay, here's the codes for this keyboard. I'm not sure of a model number, but its a Dynex, and these are the extra keyrow keys and accompanying codes. It appears I do not have this hotkey stuff installed, is it in a repository?

EDIT: My keyboard isn't supported, but I'll try editing the file. where is ".hotkeys/"? My home folder?

BACK: 234
FOWARD: 233
STOP: 232
REFRESH: 231
SEARCH: 229
FAVORITES: 230
HOME: 178
MAIL: 236
MUTE: 160
SLEEP: 223
VOLUME LOWER: 174
VOLUME HIGHER: 176
PLAY/PAUSE: 162
STOP: 164
REWIND: 144
FASTFOWARD: 153
MEDIA PLAYER: 237
MY COMPUTER: 235
CALCULATOR: 161

---

### Post by vidak on 2006-05-16
You probably won't find it in a repository, you have to make your own, but it's quite easy:
You should first make a .hotkeys directory in your home folder. (sorry I forgot to mention that :))
Now let's make a config file for your keyboard (in ~/.hotkeys), and call it dynex.def. It should look like this:
<?xml version="1.0"?>

<definition>

  <config model="Dynex Keyboard">

    <VolUp        keycode="176"/>
    <VolDown      keycode="174"/>
    <Mute         keycode="160"/>

    <Email        keycode="236"/>

    <userdef keycode="162" command="dcop amarok player playPause">Amarok Play/Pause</userdef>
...
  </config>

</definition>

You can put all the keycodes in this configfile.
Now edit the ~/.hotkeys/hotkeys.conf (first copy it from /etc)

The interesting parts:
...
### Specify the default keyboard  (without the .def extension) so you
### don't need to specify -t every time
Kbd=dynex
...
Play=dcop amarok player playPause
Stop=amarok -s
PrevTrack=amarok -r
NextTrack=amarok -f

WebBrowser=firefox
Email=mozilla-thunderbird
...

This file is quite easy to understand... Tell me if it works..

---

### Post by Wr8EYilK8Y on 2006-05-16
I'll try it when I get home. I see how it works (and yes, I installed hotkeys)

---

### Post by Wr8EYilK8Y on 2006-05-17
This does not seem to be working for me. Output flooded the Konsole and gave this as what I could reach (the rest drifted away)

```

/home/williamd/.hotkeys/dynex.def:1: parser error : Blank needed here
<?xml version="1.0">
                   ^
/home/williamd/.hotkeys/dynex.def:1: parser error : parsing XML declaration: '?>' expected
<?xml version="1.0">
                   ^
/home/williamd/.hotkeys/dynex.def:23: parser error : Opening and ending tag mismatch: WebBrowser line 12 and config
</config>
         ^
/home/williamd/.hotkeys/dynex.def:25: parser error : Opening and ending tag mismatch: Email line 11 and definition
</definition>
             ^
/home/williamd/.hotkeys/dynex.def:26: parser error : Premature end of data in tag config line 5

^
/home/williamd/.hotkeys/dynex.def:26: parser error : Premature end of data in tag definition line 3

^

```

EDIT: Fixed the opening header. now I just get this:
```

/home/williamd/.hotkeys/dynex.def:23: parser error : Opening and ending tag mismatch: WebBrowser line 12 and config
</config>
         ^
/home/williamd/.hotkeys/dynex.def:25: parser error : Opening and ending tag mismatch: Email line 11 and definition
</definition>
             ^
/home/williamd/.hotkeys/dynex.def:26: parser error : Premature end of data in tag config line 5

^
/home/williamd/.hotkeys/dynex.def:26: parser error : Premature end of data in tag definition line 3

^


```

---

### Post by vidak on 2006-05-18
could you post the whole config file?

---

### Post by Wr8EYilK8Y on 2006-05-18
```

<?xml version="1.0"?>

<definition>

<config model="Dynex Keyboard">

<VolUp keycode="176"/>
<VolDown keycode="174"/>
<Mute keycode="160"/>

<Email keycode="236">
<WebBrowser keycode="178">

<userdef keycode="162" command="dcop amarok player playPause">Amarok Play/Pause</userdef>
<userdef keycode="164" command="amarok -s">Amarok Stop</userdef>
<userdef keycode="144" command="amarok -r">Amarok Rewind</userdef>
<userdef keycode="153" command="amarok -f">Amarok FastFoward</userdef>
<userdef keycode="237" command="amarok">Amarok</userdef>
<userdef keycode="235" command="konqueror">Konqueror</userdef>
<userdef keycode="161" command="SpeedCrunch">Calculator</userdef>


</config>

</definition>

```

---

### Post by vidak on 2006-05-18
it looks like 
<Email keycode="236">
<WebBrowser keycode="178">

should end with /> like
<Email keycode="236"/>
<WebBrowser keycode="178"/>

Does it work this way?

---

### Post by Wr8EYilK8Y on 2006-05-18
it seems to work. I'm going to test its functions, k?

EDIT: It works flawlessly. How do I get Kubuntu to load it automatically (dynex.def) upon startup? And do you know the firefox arguements for foward, backward, stop, refresh, search, and favorites?

---

### Post by Wr8EYilK8Y on 2006-05-18
Also, the Amarok functions don't always work. Know why?Also, when they do, they work 3 times (fast fowards 3 times, or opens 3 times)

---

### Post by vidak on 2006-05-19
If you don't want to specify the keyboard type on every startup

### Specify the default keyboard  (without the .def extension) so you
### don't need to specify -t every time
Kbd=dynex

there should be lines like these in hotkeys.conf.
To start hotkeys automatically with kde, simply make a simlink of hotkeys to ~/.kde/Autostart using
ln -s /usr/bin/hotkeys .kde/Autostart 

for firefox command-line issue see
[http://www.mozilla.org/unix/remote.html](http://www.mozilla.org/unix/remote.html)
[http://kb.mozillazine.org/Command_line_arguments#For_Linux_and_Mac_OS_X_users](http://kb.mozillazine.org/Command_line_arguments#For_Linux_and_Mac_OS_X_users)
however I couldn't find anything according to moving in history.
I use the back/forward buttons to change music tracks I am currently listening to - the moving in history in firefox can be done much more easily through the MouseGestures plugin
[https://addons.mozilla.org/firefox/39/](https://addons.mozilla.org/firefox/39/)
[https://addons.mozilla.org/firefox/12/](https://addons.mozilla.org/firefox/12/) (I am using this one)
or 
[https://addons.mozilla.org/firefox/29/](https://addons.mozilla.org/firefox/29/)

for the search button you could use kfind or
firefox -remote "openurl(http://www.google.com)" alternatively
firefox -remote "openurl(http://www.google.com,new-window)" or
 firefox -remote "openurl(http://www.google.com,new-tab)" 
for refreshing the page you can use F5 (I have no idea, why would somebody put a button like this on a keyboard - this feature is even present in M$...)

---

### Post by vidak on 2006-05-19
what command do you use for amarok?

---

### Post by Wr8EYilK8Y on 2006-05-19
amarok
that dcop one you gave me
amarok -f
amarok -r
amarok -s

---

### Post by vidak on 2006-05-19
does it always do everything 3 times? All the commands act like this, or just these ones? 
What happens if you check these buttons with xenv? Do these buttons produce a single event?

---

### Post by Wr8EYilK8Y on 2006-05-19
I believe the one that starts with "dcop" uses it only once, but I have no way of telling. And the xev only reads 1 event each time its pressed. And Amarok is the only one reading multiple times.

---

### Post by vidak on 2006-05-20
in this case you could try to change the other console commands to dcop:
for stop eg.:
dcop amarok player stop
For full list try 
dcop amarok player 
in a console

---

### Post by Wr8EYilK8Y on 2006-05-22
Will do tonight

---

### Post by Wr8EYilK8Y on 2006-05-23
Still did not work. I did as instructed, now it runs the command 4 times.

---

### Post by vidak on 2006-05-23
Sorry I got no idea what the heck could just be happening... :(

---

### Post by Wr8EYilK8Y on 2006-05-24
I figured it out. There's no way to stop an instance of hotkeys, so every time I modified the Def file, it started a new one so it executed commands once per instance. It works now.

EDIT: Example? I ran it 2-3 times by accident and it would run the shortcut 2-3 times

---

### Post by vidak on 2006-05-24
yep. you should use eg
killall hotkeys
hotkeys
every time after modifying the configs... :)
It can be done using one command only, but I don't remember which one... :(

---

### Post by Wr8EYilK8Y on 2006-05-24
Either way it works now. Thanks!

EDIT: Any way to add "sudo mount /dev/hdb1 /media/hdb1/ -t captive-ntfs" to the boot commands? Adding the appropriate command to fstab freezes the boot sequence.

---

### Post by vidak on 2006-05-24
sure.
I think you tried to use something like
/dev/hda7       /stuff          ext3    auto        0       2
in /etc/fstab, which made the boot freeze/slow... it sounds weird..
If you mount this partition manually is everything OK?
You could try maybe to put a script in /etc/init.d which mounts the partition, or if you feel it's more comfortable to have this script runned when KDE is starting put it in ~/.kde/Autostart - you should have the privileges to use mount in this case...

---

### Post by Wr8EYilK8Y on 2006-05-25
"Only root wants to run mount"


and if I mount hdb1 in fstab as ntfs, I can't write to it. If I do captive-ntfs, it freezes there with a blinking cursor, and stops. If I mount it as captive-ntfs already logged on, I have to use sudo and run it with "Run it in Konsole" options enabled to enter the password..

---

### Post by vidak on 2006-05-25
you can mount drives using -o rw
or there is an option like user or anything...

---

### Post by Wr8EYilK8Y on 2006-05-25
Eh, its not too much trouble to use my link on the desktop

---

### Post by vidak on 2006-05-26
geez... I've read your post again, and just realized that we are speaking of a ntfs partition. It's been always hard to use ntfs-disks correctly... You can mount it (even at start), but for some reason only root can write to it...
I have the same problem too... I just use sudo mc for copying to the ntfs-disk

---

### Post by Wr8EYilK8Y on 2006-05-26
I use the captive drivers. I'm backing up the files and reformatting anyway so it looks like this.

100GB (93.6 Actual)
|
|-30GB (Music, pictures)
|
|-15GB (Adamantix Linux)
|
|-15GB (Ubuntu Linux)
|
|-15GB (PC Linux)
|
|-10GB? (Or whatever leaves 1GB for swap) (Some other linux flavor)
|
|-Remaining space is swapspace, shared by all


Or something similar

---

### Post by vidak on 2006-05-26
and your problem is, that you can't write ntfs-partitions:

---

### Post by Wr8EYilK8Y on 2006-05-28
I can write individual files. Deleted files never go away. I'm backing it up and reformatting it as I type, so this problem should disappear very soon.

---

### Post by vidak on 2006-05-29
:D
I have a similar problem with the flashdrive (or whatever) in my phone - I can delete/write anything on it, but after umounting&remounting the new files aren't there. There is however a workaround - if I mount it as root, manually, with options 
-o rw,sync
then copy the files, then do a sync, and umount... it works. This happens only with my phone, it's OK with pendrives...
it's interesting, anyway... :)

---

