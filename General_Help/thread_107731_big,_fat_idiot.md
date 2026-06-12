---
title: "big, fat idiot"
date: 2005-12-23
forum: General Help
---

### Post by caspianrocks on 2005-12-23
[that should have been my damned username...:rolleyes: ]

hello. i am a reformed windows user. well, my husband's working on teaching me more about the ways of linux, but i'm currently stuck using my mom's mac, at least for internet access. i'll get into more about me later, but for now...

*** HELP!!! ***

i bought my husband an mp3 player (microtek mh-210) for xmas and have no idea how to make it work with ubuntu (i think he's got 5.10 installed, but i'm not sure). i know he's going to have all kinds of fun messing around with it himself, but i'd really love to get at least a few albums worth of music onto it before i give it to him tomorrow.

time is incredibly short. normally i wouldn't post my phone number, but i'm in crisis mode. i'll try to stay online as long as possible, but after that (up until 2am eastern US time) you may reach me at: 207-459-4784.

thanks in advance!! *kelly

ps: if this post is out of its league, let me know, and i'll head over to the newbies section.

---

### Post by fordfan753 on 2005-12-23
Most things like that will plug into a USB port on the computer. And on 5.10, it should pop up a window a few seconds after you plug it in. When this happens you can copy, or drag and drop music to it. Always wait a few minutes or unmount it properly before taking it out, as you can corrupt data on there if you don't.

---

### Post by matthewv on 2005-12-23
It does plug into the usb port, according to the company's specs... (btw.. can anybody else access [www.microtekusa.com](www.microtekusa.com), it seems to be down:( ) so I would just try plugging it in and seeing what happens.

---

### Post by fordfan753 on 2005-12-23
I can access it fine

---

### Post by caspianrocks on 2005-12-23
pop up where? just BANG! there it is? if so, that's not doing it. could you maybe steer me in the direction to look and see whether it's being detected? i think my husband said it might just get recognized as an external hard drive.

(ps, thanks for your quick replies. i'm totally freaking out here, but it's nice to have a little support. :KS )

---

### Post by fordfan753 on 2005-12-23
Yeah, most of them I've seen will pop up a file browser on the screen.

Try clicking Places > Computer, and see if it's shown up in there.

---

### Post by caspianrocks on 2005-12-23
i might not be using 5.10 after all...

crap-ola.

---

### Post by fordfan753 on 2005-12-23
try in terminal:

```
sudo mkdir /media/mp3
sudo mount /dev/sda /media/mp3
```

---

### Post by caspianrocks on 2005-12-23
terminal sez:

mount: special device /dev/sda does not exist

grr...

---

### Post by matthewv on 2005-12-23
You could try changing /dev/sda to /dev/sda1 (just a shot in the dark) You could try substituting the 1 with 2, and try a few more numbers...

Does the command ```
lsusb
``` give you anything relating to the device??

EDIT: You could also see if the thing shows up in System --> Administration --> Disks, or whether any of the audio software like Rhythmbox or AmaroK picks up its presence...

---

### Post by fordfan753 on 2005-12-23
[QUOTE=matthewv]You could try changing /dev/sda to /dev/sda1 (just a shot in the dark) You could try substituting the 1 with 2, and try a few more numbers...

Does the command ```
lsusb
``` give you anything relating to the device??[/QUOTE]

/dev/sdb /dev/sdc /dev/sdd might also work, try them

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=caspianrocks]i might not be using 5.10 after all...

crap-ola.[/QUOTE]
You might be able to mount it manually.  Unplug it, wait about 20 seconds, plug it back in, and then type:
```

$ dmesg | grep '/dev'

```
Post the results.
Hopefully, this will give us some clue as to what device-file Ubuntu assigns to the device.

It should be something like /dev/sdb1, or something similar.

Once we have that, we can try to mount it.

---

### Post by caspianrocks on 2005-12-23
sez:

Bus 002 Device 004: ID Oedi:7636 WinMaxGroup

the other listed are just the keyboard and mouse.

---

### Post by caspianrocks on 2005-12-23
/dev/scsi/host0/bus0/target0/lun0:SCSI error : <0 0 0 0> return code = 0x10070000

this came up 4 times, with the "0" after "host" and the first of the "<0 0 0 0>" zeroes changing to 1, 2, and 3, respectively.

i'm so freakin' lost...

---

### Post by fordfan753 on 2005-12-23
I'm actually a little lost myself

---

### Post by matthewv on 2005-12-23
so trying the /dev/sda1, /dev/sdb, /dev/sdc1, etc... so on.. didn't work???

---

### Post by caspianrocks on 2005-12-23
fordfan, it called "sdb" a special device and said it didn't exist. i tried "sdc" and it went nuts: "So far the informational part. Next the mounting. ...note that one does not really mount a device, one mounts a filesystem (of the given type) found on the device." [some other stuff there in between. i'm online using a diff, not networked, computer from the one i'm working on, so i can't cut and paste code to show you all- gotta type it in. :mad: ]

---

### Post by az on 2005-12-23
1.  You rock for buying him such a nice gift.

2.  You rock for hacking away at getting it to work in Ubuntu.  And adding some songs to it.

3.  On page 40 of the manual
[http://www.support.microtek.com/product_dtl_2.phtml?prod_id=136](http://www.support.microtek.com/product_dtl_2.phtml?prod_id=136)
it says it is a usb mass storage device.  It should at least mount.


Have you tried rebooting?

---

### Post by az on 2005-12-23
Reboot.  Open a terminal type

tail -f /var/log/messages
and plug the device in.  Wait a few seconds and post what it says.  If it is having hardware trouble talking to the device, you will see errors.  If not, it will at least tell you what device it is using (sda1, sdb1....etc..)

---

### Post by fordfan753 on 2005-12-23
Hmm...try things like /dev/sdc1 I have seen these errors before, but it was so long ago that I just don't remember how I got it working.

---

### Post by The Mekon on 2005-12-23
I haven't seen anybody ask you to open your file browser (Applicationc/Accessories/File Browser).  Click up until you can go no further.  Open the Media Folder and see if you have a usb disk present.  If so you should be able to open it and drag mp3 files on to it.  Otherwise somebody with better knowlege than me is required.

Second thought have you clicked System/Preferences/Removable Drives and Media and made sure that you can Mount Removable Drives when Hot Plugged.  If not, do so and try plugging your mp3 player in again.

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=caspianrocks]/dev/scsi/host0/bus0/target0/lun0:SCSI error : <0 0 0 0> return code = 0x10070000

this came up 4 times, with the "0" after "host" and the first of the "<0 0 0 0>" zeroes changing to 1, 2, and 3, respectively.

i'm so freakin' lost...[/QUOTE]
OK, not exactly what we were after, but close.  Try:
```

$ dmesg | tail -20

```
This is what I get when I plug in my pen drive:
```

[4304875.223000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[4304875.561000] Initializing USB Mass Storage driver...
[4304875.578000] scsi2 : SCSI emulation for USB Mass Storage devices
[4304875.602000] usb-storage: device found at 2
[4304875.602000] usb-storage: waiting for device to settle before scanning
[4304875.603000] usbcore: registered new driver usb-storage
[4304875.603000] USB Mass Storage support registered.
[4304880.605000]   Vendor: VIKING    Model: USB FLASH DRIVE   Rev: 1.10
[4304880.605000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
[4304880.631000] SCSI device sdb: 125952 512-byte hdwr sectors (64 MB)
[4304880.636000] sdb: Write Protect is off
[4304880.636000] sdb: Mode Sense: 23 00 00 00
[4304880.636000] sdb: assuming drive cache: write through
[4304880.661000] SCSI device sdb: 125952 512-byte hdwr sectors (64 MB)
[4304880.664000] sdb: Write Protect is off
[4304880.664000] sdb: Mode Sense: 23 00 00 00
[4304880.664000] sdb: assuming drive cache: write through
[4304880.664000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4304880.682000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
[4304880.693000] usb-storage: device scan complete

```
You should get something similar.  The bit that concerns you is where it says "SCSI device sdb: 125952 512-byte hdwr ".  For you, the device may be something different, but once you puzzle it out, that is the device we have to use.

---

### Post by caspianrocks on 2005-12-23
umm... does reboot equal restart?

(remember the post title: big, fat idiot here.)

---

### Post by fordfan753 on 2005-12-23
[QUOTE=caspianrocks]umm... does reboot equal restart?

(remember the post title: big, fat idiot here.)[/QUOTE]

It does, but it really shouldn't be neccesary.

---

### Post by matthewv on 2005-12-23
[QUOTE=caspianrocks]umm... does reboot equal restart?

(remember the post title: big, fat idiot here.)[/QUOTE]
usually

---

### Post by caspianrocks on 2005-12-23
cwald: i got nothing of the sort, just "scsi error".

mekon said: "I haven't seen anybody ask you to open your file browser (Applicationc/Accessories/File Browser). Click up until you can go no further. Open the Media Folder and see if you have a usb disk present. ... Second thought have you clicked System/Preferences/Removable Drives and Media and made sure that you can Mount Removable Drives when Hot Plugged."

if i could access anything that looked happy and slashey like the places you wrote, i'd be a lot better off than i am.

*rant* i swear sometimes that my husband only uses linux to keep me from accomplishing ANYTHING on my computer. idiot though i am, windows was just more accessible for dumbasses like me... i could hunt and peck my way out of practically anything. here, i feel like if i don't know any code (and i certainly don't) i'm at a complete loss.

---

### Post by caspianrocks on 2005-12-23
rebooting now. gotta head downstairs to caffeinate myself for the long haul and feed my toddler (who has been remarkably patient thus far). brb asap, ttfn... lol. :rolleyes:

---

### Post by fordfan753 on 2005-12-23
It can be difficult to be dumped straight into a command line to try to fix something, but for me that's half the fun, it's just like a big learning curve, if you stick with it and eventually get it working you'll feel a great sense of self achievement.

---

### Post by az on 2005-12-23
This could be as simple as the husband having disabled the automatic mounting in the gnome device manager.  

Sometimes, it keeps assigning a different device each time you plug and unplug (bug) that I whay I suggested the reboot.

---

### Post by fordfan753 on 2005-12-23
It's possible, but dmesg is reporting errors, so I don't think it's the underlying cause.

---

### Post by The Mekon on 2005-12-23
I am sorry if I appear to be too simple but I often find that most problems are fairly basic.

When I use a slash I meant the next level in a menu.

In my first question I meant you to go to the top left hand corner of your normal window and Click on Applications which shows a drop down menu.  Then click on Accesories which brings up another menu.  Next click on File Browser which will open in you Home directory.  Click on the Up Arrow twice and it will dissappear as you have got to the top directory /.

Now you will fin a folder called Media which you should open to see if your mp3 player has been automatically detected as a usb disk.  If so you open it and drag you mp3 files in to it.

My second thought was (following the same procedure as above) was to click on System then Preferences followed by Removable Drives and Media.  Here you can set preferences are I suggested before.

If you have done all this and you can't see your mp3 player you may hve a more difficult problem.

---

### Post by caspianrocks on 2005-12-23
yah, i know what the slashes are for. what i meant was that i can't access anything like that. i can't get to applications/accessories or system/preferences. whatever version of ubuntu i'm using, it's not very moron-friendly. also, it's presumably pretty old, because my husband hasn't been able to dl new upgrades (damned dial-up). we just got out 5.10 disks in the mail a few days ago, but he hasnt had a chance to install it yet.

---

### Post by caspianrocks on 2005-12-23
okay, major breakthrough. the media folder is indeed now detecting the mp3 player. huzzah! (mekon, i swear it wasn't there before!) still, it won't let me just copy and paste the files in there... possibly because when i was ripping our cds, my husband had me put them in ogg-vorbis format instead of mp3. [he said this might be an issue.]

---

### Post by matthewv on 2005-12-23
Do you have the right permissions to access it...? What error message do you get when you try to copy files across... (I don't think that mp3 player supports ogg... try using a program like SoundConverter to convert your ogg to mp3, but that shouldn't stop you from copying files over)...

---

### Post by caspianrocks on 2005-12-23
nope, the mp3s wont copy either.

---

### Post by matthewv on 2005-12-23
[QUOTE=caspianrocks]nope, the mp3s wont copy either.[/QUOTE]
Error message..??

---

### Post by fordfan753 on 2005-12-23
```
sudo cp /path/to/mp3 /media/mp3player
```
Try that, since it might need to be copied as root, if that works then we know it's a permission thing.

---

### Post by caspianrocks on 2005-12-23
just switched to my husband's username, which should give me supreme access, but it's still not working.

---

### Post by caspianrocks on 2005-12-23
fordfan: that gave me the following...

cp: cannot stat `/path/to/mp3' : no such file or directory


matt: no error message because i was just trying to drag'n'drop through konqueror (trying to avoid the dreaded terminal, if at all possible).

---

### Post by fordfan753 on 2005-12-23
What I meant was find an mp3, find out the location, and then substitute it into /path/to/mp3 sorry if I wasn't very clear

---

### Post by caspianrocks on 2005-12-23
how exactly should i type in what you're talking about (including mp3 file name and all)? it's not a matter of you being unclear, it's just me being awfully dense.

---

### Post by caspianrocks on 2005-12-23
tells me that /media/mp3player specified destination directoy doesn't exist. ditto for /path/to/mp3 ...then it said try cp --help fmi

---

### Post by fordfan753 on 2005-12-23
```
ls /media
```

---

### Post by caspianrocks on 2005-12-23
entered:
ls /media

got:
cdrom cdrom0 cdrom1 floppy floppy0 mp3
(in lovely blue and turquoise)

---

### Post by fordfan753 on 2005-12-23
What you need to do now is find the music you want to put on it, and drag it to your desktop, then you can try

```
sudo cp /home/*username*/Desktop/*file.mp3* /media/mp3
```

---

### Post by caspianrocks on 2005-12-23
gotta run :(  it's time for my prince caspian to catch some zzzs. i should be back in an hour or so. if any of you are still kicking around, i'll be so grateful. 

thanks to EVERYONE for your help thus far. you were all so kind to immediately hop on this thread and try to bail me out. have a healthy and peaceful holiday season. :KS 

back in a flash...

---

### Post by The Mekon on 2005-12-23
First you should sort out the permissions for the mp3 player.

While in the File Browser Right Click on the mp3 player folder to bring up a menu.  At the bottom click on Properties and on the next page click on Permissions.  You should be be able to see the Group the folder belongs to,  and the read/write permissions.  There should be ticks for Owner Read, Write and Execute.  If not, tick them if you (or your husband) are the owner.  


Now while still in the File Browser can you open the disk and see its contents?  If so explore the disk by opening and closing any folders to try and find any mp3 file which may have been been installed as sample music.  (My wife's mp3 player came with a sample folder of music).  Note where the samples are and copy you mp3 file to folders in the same area.

---

### Post by caspianrocks on 2005-12-23
cannot stat blah/blah/desktop/filename.mp3 /media/mp3... no such file or directory

---

### Post by caspianrocks on 2005-12-23
sez only owner (root) can change permissions. logged out of my session and tried to use "root" as my username. said i can't log in as root, although it seemed to like the password i used. how can i get around this?

---

### Post by fordfan753 on 2005-12-23
Open nautilus as root and do permissions that way
```
sudo nautilus
```

---

### Post by caspianrocks on 2005-12-23
[QUOTE=The Mekon]Now while still in the File Browser can you open the disk and see its contents?  If so explore the disk by opening and closing any folders to try and find any mp3 file which may have been been installed as sample music.  (My wife's mp3 player came with a sample folder of music).  Note where the samples are and copy you mp3 file to folders in the same area.[/QUOTE]

open disk and see its contents, wha-? i don't think there are any sample files on mine...

---

### Post by caspianrocks on 2005-12-23
'kay, opened nautilus, but now what? (baby steps...)

---

### Post by ninotob on 2005-12-23
Too many cooks perhaps, but here's an idea if you are somewhat comfortable following instructions for the command line.  It would copy all your files in one fell swoop (with caveats for spacey filenames).

First, be logged in as yourself, not your husband (I'm assuming you ripped the cds in your account and not his).  Then open "terminal" (applications, accessories, terminal).

See if this command lists all of the songs you have ripped:

```

find -name "*.mp3"

```

if yes, do they have spaces in the filenames?  Are there spaces in the directory names?  If the answer is NO,

you can easily transfer them all with this line:

```

for i in $(find -name "*.mp3"); do sudo cp $i [COLOR="Red"]/media/mp3player[/COLOR]; done;

```

**EDIT:  replace "mp3" if they are really all "*.ogg" files (or whatever the ogg vorbis extension is -- I haven't used ogg much).**

Assuming the red higlight describes the directory of your mp3player.

What this does is issue the find command which lists the path from your search point to the matching files.  It assigns the find results to the variable "i" (denoted as $i when it is used).  Then it does a copy (cp) of the matched files to the target directory (in red).  Then it's done.  Note, I used "sudo" because you mentioned being unable to copy to the drive.  That should handle that issue.

It becomes a bit more complicated with spaces in directory names, at least I'm having trouble escaping the spaces.

OT:  guru's??  why does this:  *find -name "*.mp3" | sed -e 's/\ /\\\ /g'* generate the correct output on the cli, but it won't work in the "for in" line above -- even if I quote the variable in the cp command, and even if I do "'"$i"'" in the cp command?

---

### Post by caspianrocks on 2005-12-23
weird. tried that and it just gave me the 2 mp3s on the desktop, as well as one that said "incoming".

---

### Post by caspianrocks on 2005-12-23
[QUOTE=fordfan753]What you need to do now is find the music you want to put on it, and drag it to your desktop, then you can try

```
sudo cp /home/*username*/Desktop/*file.mp3* /media/mp3
```[/QUOTE]

okay, i just tried this again and it copied the file to the mp3 folder. it's not actually coming up on the mp3 player itself though. do i have to export somehow?

---

### Post by caspianrocks on 2005-12-23
for i in $(find -name "*.mp3"); do sudo cp $i /media/mp3player; done;

did this. sez permission denied. how the crap do i get permission??

---

### Post by hoodwink on 2005-12-23
Ican't help with this, but I must say you ask a lot more intelligent questions than the average big fat idiot <g>. Keep trying.

---

### Post by matthewv on 2005-12-23
for permission... you could try a ```
sudo chmod -R 777 /media/mp3/
``` careful with that command though.. if you execute it in the wrong spots it can be a bit of a problem... if you run it exactly as typed you should be okay, just make sure to use "-R" not "-r"

---

### Post by SickTwist on 2005-12-23
Caspianrocks,
I'm honestly not trying to sound like Captain Killjoy but do you realize that the MH-210 does not play Ogg Vorbis music? It only supports patent-encumbered formats (MP3, VBR MP3, WMA, WMA DRM) and it sounds like your husband is trying to avoid these since he prefers to encode in Ogg Vorbis. Perhaps another player would play more nicely with Free Software and Ubuntu.

---

### Post by caspianrocks on 2005-12-23
sweet merciful monkeys. i just switched back to my desktop, because someone suggested that may be the cause of my permission problems. then i entered this again:

for i in $(find -name "*.ogg"); do sudo cp $i /media/mp3player; done;

and the terminal just went freakin' CRAZY. i can barely read it because it's (still) spitting out the names of every music file on the entire computer, followed by something like

cp: cannot stat: 'blah': no such file or directory

the problem is that, in the 'blah' part, it's not listing the complete names of songs/files, just bits and pieces, like "Floyd/pink" and "dark" and "side", all disjointed.

oh, thank goodness, it just stopped. [i'm a filthy, pirating thief, so i was afraid it was going to go on all night.]

---

### Post by matthewv on 2005-12-23
a ctrl+c would have stopped that straight away :). So what is the name of the folder for your mp3 player... in /media... Did you try chmod... as i said above??

---

### Post by caspianrocks on 2005-12-23
sicktwist: no prob. he seemed determined to use the ogg format, claiming he can make it work... somehow. for tonight though, i'll stick to the mp3s. thanks for saving me the time of trying to do the ogg ones.

hoodwink: thanks for the pep talk. that plus a bit more caffeine should keep me going to see this through.

ninotob: tried the same line of code, replacing ogg with mp3, but the same thing happened.

matt: now that i've switched back to my own username, the permission prob seems to be alleviated. name of my folder is simply media/mp3. thanks for ctrlC tip.

---

### Post by caspianrocks on 2005-12-23
See if this command lists all of the songs you have ripped:

find -name "*.mp3"

just tried this again, now that i'm steering clear of OGG. it worked and it didn't... some of the filenames came through just fine, but others were missing pieces (like i mentioned before when i tried to do the all-at-once copy command).

---

### Post by caspianrocks on 2005-12-23
okay, my son caught a second wind for a while, but it just blew out the window. i should be back in 1/2hr or so. thanks again to you all!!!

---

### Post by SickTwist on 2005-12-23
Try this command exactly like it is typed (you can just copy and paste it into a terminal):

sudo find -L /home -iname '*.mp3' -exec cp -f '{}' /media/mp3 ';'

That command will copy *all* files that end in .mp3 .Mp3 .MP3 or .mP3 from any subdirectories in /home to the /media/mp3 directory (which is where the player is mounted).

---

### Post by ninotob on 2005-12-24
That would be because you need to change the part in red to reflect your media player directory -- in this case (based on chmod suggestion above) -- it appears your player is at /media/mp3

What you saw in the terminal was it just saying for each file that it couldn't copy to the /media/mp3player directory because it doesn't exist.

What exactly is your mp3 player directory?  replace the /media/mp3.... line with that directory path.

EDIT: nevermind -- go with SickTwist's suggestion.

---

### Post by caspianrocks on 2005-12-24
sez: invalid predicate `-L'

---

### Post by ninotob on 2005-12-24
deleted, I should read to end before posting.  ;-)

---

### Post by ninotob on 2005-12-24
[QUOTE=caspianrocks]sez: invalid predicate `-L'[/QUOTE]

Try by omitting "-L" -- that's to follow symbolic links -- I doubt you made your links to your files.

---

### Post by ninotob on 2005-12-24
Caspian -- SlickTwist's line is really great, it even works with filenames that have spaces in them.  Just tested.  ;-)  As I mentioned before, mine doesn't handle spaces.

Just use it without the "-L", like this:

```

sudo find /home -iname '*.mp3' -exec cp -f '{}' /media/mp3 ';'

```

---

### Post by caspianrocks on 2005-12-24
when i ask to list all the mp3s it can find, it comes up with a pretty comprehensive list. then when i type in your code (for i in $ find -name ...etc), it sez: 

cp: cannot stat `Music/They': no such file or directory
cp: cannot stat `Might': no such file or directory
cp: cannot stat `Be': no such file or directory
cp: cannot stat `Giants/They': no such file or directory

instead of giving the filename in its entirety.

---

### Post by caspianrocks on 2005-12-24
Try by omitting "-L" (said ninotob the magnificent)



it's freakin' working! it's copied 204 files and still counting.

so, for my final task, how in blazes do i get the files from the mp3 folder to the player itself??

(and, a somewhat digressive post-script: any ideas where to look for more info re my husband's quest to use the ogg files? i think he said something about putting new software onto the mp3 player itself that could read ogg. unfortunately, we have no broadband at the moment, so it might be easier to just convert the damned things.)

---

### Post by SickTwist on 2005-12-24
Glad it worked.

Ogg  Vorbis and MP3 are both lossy codecs (meaning they each contain less audio data than the original CD, that is why they take up less space). It is generally a bad idea to convert from one lossy codec to another. It's kind of like using a copy machine to make a copy of a copy of a copy... the page just gets more and more blurry.

---

### Post by fordfan753 on 2005-12-24
[QUOTE=caspianrocks]Try by omitting "-L" (said ninotob the magnificent)



it's freakin' working! it's copied 204 files and still counting.

so, for my final task, how in blazes do i get the files from the mp3 folder to the player itself??

(and, a somewhat digressive post-script: any ideas where to look for more info re my husband's quest to use the ogg files? i think he said something about putting new software onto the mp3 player itself that could read ogg. unfortunately, we have no broadband at the moment, so it might be easier to just convert the damned things.)[/QUOTE]

You wont get the thing to play oggs, I think most of these players would probably have the software on a ROM chip, which means no playing around with new software.

---

### Post by SickTwist on 2005-12-24
By the way, don't forget to do this command before unplugging the player:

sudo umount /media/mp3

That tells the computer that you have finished using the device.

---

### Post by caspianrocks on 2005-12-24
so, aside from ripping my cds as mp3s from now on, how'm i gonna get the ones that are already oggish (there are quite a few) to work for me? can i use windows media or another format? i get what you're saying about a "copy of a copy", but still...

and i'm still kinda stuck here. i'm showing a nice, full "media/mp3" folder, but an empty mp3 player. how can i get them on board?

---

### Post by caspianrocks on 2005-12-24
sez: /media/mp3: not mounted

that kinda sounds bad...

---

### Post by fordfan753 on 2005-12-24
That is bad...that means that we're right back near step 1, getting the thing to mount

---

### Post by SickTwist on 2005-12-24
[QUOTE=caspianrocks]so, aside from ripping my cds as mp3s from now on, how'm i gonna get the ones that are already oggish (there are quite a few) to work for me? can i use windows media or another format? i get what you're saying about a "copy of a copy", but still...

and i'm still kinda stuck here. i'm showing a nice, full "media/mp3" folder, but an empty mp3 player. how can i get them on board?[/QUOTE]

I'm confused--I thought that /media/mp3 is where the player was mounted... If the player is not mounted then we are back to square one...

Regarding the ogg files: That is the point I was making earlier. There is no easy way to play them on this particular player without really messing up their quality.

There are [many other players]("http://wiki.xiph.org/index.php/PortablePlayers") that support Ogg Vorbis and most of them will probably play MP3 as well.

---

### Post by caspianrocks on 2005-12-24
sicktwist wrote:

I'm confused--I thought that /media/mp3 is where the player was mounted... If the player is not mounted then we are back to square one...

* well, i have a folder for media/mp3. it's all fat and jolly, full of song files. but there are no songs on the player.

azz wrote: 

tail -f /var/log/messages
and plug the device in. Wait a few seconds and post what it says.

* it said: 

tail: cannot open ` /var/log/messages’ for reading: Permisson denied
tail: no files remaining

matt wrote:

so trying the /dev/sda1, /dev/sdb, /dev/sdc1, etc... so on.. didn't work???

* i just retried sda, sdb, sdc, and sdd, as well as 1, 2, and 3 on each, with zero success.

---

### Post by fordfan753 on 2005-12-24
What does "dmesg" have to say when you plug it in?

---

### Post by caspianrocks on 2005-12-24
lots and lots of stuff (remember, i'm online using a diff computer, so can't cut + paste). things that looked especially interesting:

usb-storage: device found at 9

and

Buffer I/O error on device sda, logical block

if you ask me to look for something specific in what it spit out, i can easily do that.

---

### Post by fordfan753 on 2005-12-24
The fact that it's showing sda in there is interesting...

---

### Post by caspianrocks on 2005-12-24
i typed:
sudo mount /dev/sda /media/mp3

it said:
mount: you must specify the filesystem type

---

### Post by SickTwist on 2005-12-24
Try this:

sudo mkdir /media/player
sudo mount -t vfat /dev/sda1 /media/player

If that works (doesn't give any error messages) then do this and be sure to get the spaces correct:

sudo find /home -iname '*.mp3' -exec cp -f '{}' /media/player ';' 
sudo umount /media/player

Then you can remove the player and you're done.

---

### Post by caspianrocks on 2005-12-24
mount: /dev/sda: can't read superblock

---

### Post by fordfan753 on 2005-12-24
```
sudo mount -t vfat /dev/sda /media/mp3

```

---

### Post by SickTwist on 2005-12-24
Good news: I just noticed this on the Microtek website:

- Firmware: Upgradeable (OGG audio format and MPEG4 video format) 

I haven't found the firmware yet but apparently there *is* Ogg Vorbis support (or it is planned). :)

---

### Post by caspianrocks on 2005-12-24
ditto about the superblock.

---

### Post by caspianrocks on 2005-12-24
yah, my hubby's pretty slick like that. (especially when compared with me...)

---

### Post by ninotob on 2005-12-24
[QUOTE=caspianrocks]when i ask to list all the mp3s it can find, it comes up with a pretty comprehensive list. then when i type in your code (for i in $ find -name ...etc), it sez: 

cp: cannot stat `Music/They': no such file or directory
cp: cannot stat `Might': no such file or directory
cp: cannot stat `Be': no such file or directory
cp: cannot stat `Giants/They': no such file or directory

instead of giving the filename in its entirety.[/QUOTE]

Here's a trick to learn in any nix environment:  Don't use the space bar in filenames or directories, use the underscore "_" key to denote spaces.  The reason is that a command like "cp", for example, cp [COLOR="DarkGreen"]this.text[/COLOR] [COLOR="DarkRed"]/there
[/COLOR] uses the space character to understand the difference between what you want to copy (green) and where you want to put it (red).

If you have something like this:  

cp /music there might be giants/somesong.mp3 /some directory/with spaces

what the computer sees a bunch of files named "/music", "there", "might" ... etc. and thinks you want to put it a directory called "spaces".  None of these exist so it gives you errors.

What that means is that it takes a deeper level of knowledge (like SlickTwist has) to be able to manipulate them automatically.  You can manually escape the spaces, meaning, tell the computer "this isn't part of the command structure, it's part of the name" by using the \ character or by putting the name in quotes.  Either way, it can get complicated.

For example, my original idea was to account for spaces by running the find output through an editor (called sed), but it too uses the \ character as an escape character -- so to insert an escaped space requires escaping the backslash as well.  But the hard part was that it behaved differently in my "for i in" line then it did with a plain old "find" line.  In otherwords -- complicated.  The easiest solution is to banish the space bar from file/directory names.

---

### Post by caspianrocks on 2005-12-24
wow. that was crazy detailed, but certainly useful. the next snow day, i'll sit my butt down and rename a whole lotta files. (my husband will thank you, i'm sure, since after tonight he's going to be the one dealing with all this!)

---

### Post by matthewv on 2005-12-24
The thing about the superblock seems to suggest that either the device isn't formatted or it does not use the vfat filesystem. Both seem unlikely, especially the second... Is it possible (I'm asking everyone) that the device cannot be mounted as an ordinary usb hard drive.. and that it needs its own drivers, or should be mounted from a program such as rhythmbox or amarok that support music players??? btw... does sda1 help, instead of sda

---

### Post by caspianrocks on 2005-12-24
"...should be mounted from a program such as rhythmbox or amarok that support music players???"

now that you mention it, i want to say my husband mentioned something about running it thru amarok. know how i could do this??



"btw... does sda1 help, instead of sda"

nope.

---

### Post by ninotob on 2005-12-24
You know, I don't understand why it isn't mounting under ST's directions.  I looked at some info on their website and it works with both Mac's and Windows machines (**EDIT:  this would highly suggest it's just a usb device and not some crazy special driver**).  That suggests that they are using a "vfat" partition because that'll work on both.  Their instructions aren't clear at all on how to add songs from a mac (which I'm assuming would be more linuxy than the windows instructions).  

I would suggest that you try some additional numbers after sda.  I know you've already tried ... but maybe there was a typo?  Here's a hint I'm not sure you know -- if you press the up arrow key, you can cycle up through your recently typed commands (and down through them too if you've traveled upward).

Let's go back through the first half of ST's instructions:
If you have already done this:

```

sudo mkdir /media/player

```

Don't do it again.  but make sure it is there.  type

```

cat /media/player

```

You should see something like this:

```

cat: /media/player: Is a directory

```

If you see "No such file or directory", then you need to do the mkdir command above before moving on.  Then test to make sure it's there.

Assuming you have /media/player

```

sudo mount -t vfat /dev/sda1 /media/player

```

if it fails, replace the "1" with a "2" ... go up to 9 just for kicks.  The easiest way to do this is to type the sda1 command meticulously.  Every space character is important.  If it fails, press the up arrow key, then use the left arrow key to move the cursor to the right of "1", press backspace, then press 2, then hit "enter".  It'll save time and you won't make a typo.

---

### Post by matthewv on 2005-12-24
amarok (kde/kubuntu) and rhythmbox(gnome/ubuntu) include support for the direct transfering of music to an ipod... I was just wondering if this might help..
I think you just plug the device in and hopefully it appears in amarok or rhythmbox... i know rhythmbox will show ipods and such in a column on the side...

---

### Post by caspianrocks on 2005-12-24
got the 'Is a directory' part. then sda said 'can't read superblock' again. no other sda's (or b's or c's or even d's) worked. (and, yes, i went up to nine, at least on sda. :p )

---

### Post by matthewv on 2005-12-24
Does the player show up as a device in a program such as gparted, or qtparted, or System --> Administration --> Disks (ubuntu only)?? does it show up in rhythmbox or amarok...

---

### Post by caspianrocks on 2005-12-24
matt, everything you suggested was right there. (if this works, i'm going to be pretty pissed, because it was RIDICULOUSLY easy.) how can i tell whether they've transferred or not? i can just unplug the player and check, but do i need to do anything to protect it first?

---

### Post by matthewv on 2005-12-24
I wouldn't know... I've never used either rhythmbox or amarok for portable players.. i would make sure it has finished transferring, then unplug it, or see if the media player has some option for eject or remove device.. just look round a bit.. and if you can find nothing, pull the thing out and see if it works.. it will need mp3s though.. unless the media player has automatically converted the files for you...

---

### Post by caspianrocks on 2005-12-24
"does it show up in rhythmbox or amarok..."

dunno. how can i find it? what i have is a happy section on the left of amarok called "media device browser". it tells me to "drop files here to enqueue them for transfer to your ipod."

---

### Post by matthewv on 2005-12-24
Sorry.. but what did you mean then when you said... that everything you suggested was there.. which suggestion of mine were you talking about..??

---

### Post by caspianrocks on 2005-12-24
s'okay. i don't know what time you've got, but it's almost 430am here (maine, usa) and i'm minutes away from calling it quits because i'm having trouble keeping my eyes open.

i tried going thru amarok. it had a button called "media device", which i selected. that brought up the drag'n'drop menu. i filled the queue with songs, then hit "transfer". nice and easy... except it didn't transfer - or do anything.

---

### Post by matthewv on 2005-12-24
???? Dunno.. never used that feature of amarok... maybe u better catch some sleep.. its only 5:14pm here (western australia) I've basically been following this thread since the i got up this morning till now (your first post was 8 hours ago).. :) You could try rhythmbox.. but i dont think that would do much differently.. Hopefully someone who knows more bout that will help

EDIT: I've been reading through the specs and user manual and it seems like the thing should work just like that... like any usb disk.. plug it in, transfer, unplug it. Looks like a very nice player, but I can't find the firmware update anywhere :(

---

### Post by ninotob on 2005-12-24
[QUOTE=caspianrocks]matt, everything you suggested was right there. (if this works, i'm going to be pretty pissed, because it was RIDICULOUSLY easy.) [/QUOTE]

Ha!  That's how it is supposed to work.  Rack your brain for hours and then discover just how easy it actually is.  ;-)

---

### Post by caspianrocks on 2005-12-24
yah, i'm wishing now that it had been that easy. i know my husband's going to waltz in here tomorrow and be good to go in like 10 minutes, too. that totally kills me. :mad:  still, as long as i can rock out to my favorite tunes in the car, i'll be a happy wifey.

thanks, thanks, thanks again. although this was frustrating, it's definitely given me the confidence to start messing around and learning a bit more.

(and, of course, if i wake up in a few hours and some wonderful tux-fairy has solved all my xmas problems, well... i'll just be that much more grateful, and i'm sure santa will reward your kindness. :D )

:KS kelly

---

### Post by SickTwist on 2005-12-24
Don't get too discouraged--sometimes there are pieces of hardware that cause a lot of grief in Linux. (Usually because their manufacturers do not tell the community enough details about how the hardware works.) This player may or may not get working with Ubuntu. But either way, you gave a tremendous effort and that is to be applauded. If I were your husband, the time that you spent working on this would mean more to me than anything.

By the way, if you are still interested in learning more about working on the command line in Linux after this ordeal, there are some nice tutorials here:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

The command line is very powerful in Linux. You could, for example, write a small script that automatically converts spaces to underscores in the filenames of all your MP3s. [Here]("http://www.granneman.com/techinfo/linux/scripts/spacetounderscore.htm") is an example of this (I have not tested it). Ubuntu is based on Debian so you may need to use the example near the botton that is listed under "For Debian Users".

Best wishes! :)

---

### Post by az on 2005-12-24
[QUOTE=caspianrocks]
i tried going thru amarok. it had a button called "media device", which i selected. that brought up the drag'n'drop menu. i filled the queue with songs, then hit "transfer". nice and easy... except it didn't transfer - or do anything.[/QUOTE]

Are you using kde or gnome?  In Hoary, kde used an older (not HAL) architecture for hotpluggable devices and that may be the problem.  If you are using gnome, does rythymbox work?

Also, try running amarok from the command line - that way you get to see the errors when you try to transfer files, and stuff.

If it is a permission problem, and you are under the wire, try running amarok as root (eep!)

sudo amarok

---

### Post by tardis on 2005-12-24
This may be to late and of no good.  My son's ipod would do nothing with any ubuntu under 5.10.  Sorry to say that but I tried everthing, but with 5.10 all that has changed.  He still uses iTunes but at least I can play around with it in ubuntu...

Hope this doesn't crash any hopes...

---

### Post by az on 2005-12-24
[QUOTE=tardis]This may be to late and of no good.  My son's ipod would do nothing with any ubuntu under 5.10.  Sorry to say that but I tried everthing, but with 5.10 all that has changed.  He still uses iTunes but at least I can play around with it in ubuntu...

Hope this doesn't crash any hopes...[/QUOTE]
You must mean 5.04 -> 5.10

CaspianRocks: Anyway, since you just recieved the shipit Ubuntu cds, try the live cd.  You will be able to see you ubuntu instll on the hard drive (and get the songs) and mount your media player....  I hope.

---

### Post by caspianrocks on 2005-12-24
thanks, azz. i think he's going to be more shocked than anything else, especially when i send him over here to read all my crazy posts.

gonna try the 5.10 disk now, so wish me luck. i'll be back later to report, and i'll definitely send him back later to let you all know how he manages (esp if he gets the ogg files on there), if i can't figure it myself.

---

### Post by daniel2501 on 2005-12-26
Hi all. I'm the hubby that caspianrocks was talking about above.  Thanks everyone for the help!  I actually haven't been able to get this player to work either :(  According to dmesg, the hotplug system acknowledges that the player is connected and scans the disk.  The issue is that ubuntu can't mount the filesystem on the disk because (I think) our player is just one of those USB Mass Storage Devices that sends something confusing and gives multiple SCSI errors as it tries to read the drive's contents.  It's giving an "unable to read partition table" error, in addition to I/O errors as it continues to read the drive.
I'm going to keep hacking away to get this running, but in the mean time, I guess it looks like I'll have to fire up the old Win XP partition to do anything related to mp3s. And my hopes of using just ogg to stare my music are dashed for the time being until, I guess either the hotplug system gets upgraded, or I can find something(I've heard rumors about a kernel patch that work for this type of scsi error.)

---

### Post by az on 2005-12-26
Are you running Hoary?  A lot of stuff was dfixed in Breezy...  Try the liver cd.

---

### Post by jannol on 2005-12-26
I had exactly the sam issue but with another type of mp3 player, I plugged it into win and formatted it to fat16 and then it worked automagically in breezy :)

Maybe there's a small chance it could work for you aswell.

My current mp3 player, frontier NEX IIe needs to be turned on before I plug it in the usb.

---

### Post by daniel2501 on 2005-12-26
I'm actually running Hoary, yes. I did try it with the live cd, and had the same issues.  However, it did show and icon in Computer in Nautilus, but couldn't mount because of the same SCSI errors.

---

### Post by daniel2501 on 2005-12-26
Reformatting to fat16?  I was thinking of that, but I thought that maybe it would cause the player not to work.

---

### Post by daniel2501 on 2005-12-26
Does anyone know if the cowon iAudio X5 player plays nice with ubuntu? In addition to not being easily (or maybe at all) accessible by (at least debian based) linux, it also has a perplexingly poor interface, and is missing an astonishing number of features, like a "random" setting, for one. Even if i can get it to work with my ubuntu system, I think I'm going to return it and get an X5 or an iPod Video. Don't worry, I'm not knocking my wife's present. She agrees, and besides, i was the one who picked the Microtek MH-210 anyway.

---

### Post by SFN on 2005-12-26
Since you're considering a different player, allow me to suggest going here:
[http://www.neurosaudio.com/store/prod_442.asp]("http://www.neurosaudio.com/store/prod_442.asp")

---

### Post by Substance on 2005-12-26
hmmm has she given him the player yet?

edit: sorry hijacked thread removed question, out of respect.

---

### Post by SFN on 2005-12-26
Yep. He's daniel2501 from above.

---

### Post by daniel2501 on 2005-12-26
Wow! iAudio actually *advertises* linux support on their website. A lot of hardware manufacturers don't bother to do that even if their hardware is supported. That practically sells me! Now... can i find an X5 for about $250?

---

### Post by SFN on 2005-12-26
[QUOTE=daniel2501]Now... can i find an X5 for about $250?[/QUOTE]

In many places. Froogle it.

---

### Post by daniel2501 on 2005-12-26
You know, i kinda want to try the formatting thing, just because I can't stand to let something just not work, but i'm afraid that it might cause problems with returning it

---

### Post by daniel2501 on 2005-12-26
Thanks for the froogle tip. I actually found one with regular google, but froogle found a cheaper one. You know, until we get broadband back, I feel like I'm so behind the times because i don't go online that much, and you know my kubuntu would be Breezy(and possibly KDE 3.5) if I had broadband right now!

---

### Post by daniel2501 on 2006-01-21
Hello all! I thought I'd post an update regarding our mp3 player situation.
We decided to return the Microtek MH-210 my wife had bought me for Xmas. The player's file system was not only unable to be mounted by Linux, but also not by OSX, as we found out after trying it on my friend's laptop. A *dmesg* on the Mac showed the same errors I got with ubuntu. In addition, the player's interface is hopelessly poorly designed. So we got an iAudio X5, with mounts instantly with no setup, and has a much better UI.
Thanks for all the help :)

---

