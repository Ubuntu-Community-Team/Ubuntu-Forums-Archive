---
title: "Adding AAC encoding to GRIP in Ubuntu Breezy"
date: 2005-10-24
forum: Desktop Environments
---

### Post by stuart-newtoubuntu on 2005-10-24
Hello

I am at the end of my abilities' and I need a some help, I am new to ubuntu and I am enjoying the challenges faced by linux. 

I installed GRIP and FAAC using Ubuntu's package manager, but I cannot get GRIP to create aac files, which I intend to use for my ipod. 

I have created a new setting in the grip config/encode/encoder with the following values, which I got from an audiocoding forum. 

Encoder Executable             /usr/bin/faac
Encoder command line        w -q 130 -c 19000 %w %m
Encode file extension          mp4
Encode file format              /mnt/audio/grip/%A/%d/%A - %d - %t - %n.%x

My problems are when ripping and encoding after the .wav is created I get an error message which is "no write access to write encoded file." 

I assumed that this is something to do with ownership so I changed settings and now Grip and FAAC belong to me rather than root. Even with these changes I still receive the same error message. 

Can anyone help or even suggest an alternative way of creating ipod friendly aac's? 

I have no problems with playback of aac's etc....

---

### Post by Juzz on 2005-11-01
Shouldnt' this:
> Encoder command line w -q 130 -c 19000 %w %m
Be like this:
Encoder command line **-**w -q 130 -c 19000 %w %m
notice the "-w"

However does the faac in Ubuntu support mp4 wrapping?
I can't get it going - and when I try to do a "faac --help" it says something like "mp4 support unavailable" :(

I then tried downloading the source, but I get several errors - one of them I solved by installing a lib, but still get an error about "AC_PROG_LIBTOOL".

---

### Post by Juzz on 2005-11-01
I was missing Libtool - now I can compile faad and faac...

I installed the libs and tools mentioned here:
[http://www.mail-archive.com/autoconf@gnu.org/msg11707.html](http://www.mail-archive.com/autoconf@gnu.org/msg11707.html)

Now to wait for the compile to finish ;)

---

### Post by stuart-newtoubuntu on 2005-11-01
Thanks for the help Juzz. 

I have kind of given up on the AAC encoding as transfering music to my ipod became a problem.

To get around this, I've mounted my windows partition in linux so I can access my music files and I am continuing to use itunes, for the time being.

---

### Post by Juzz on 2005-11-01
Still no MP4 support :( 

I no longer know what I can try - can anyone supply me with a version of faac that will support MP4 or give me a detailed description of how I can get it on my own?

---

### Post by stuart-newtoubuntu on 2005-11-02
I tried this when I had given up on grip. 

There is a package called Banshee, which after I installed had an option to encode into MP4. I didn't try it though. 

It can also transfer files to an ipod, although it didn't work for me. 

Banshee seemed like the most complete alternative to itunes that I tried. I'm definately planning to keep track of banshee and add hopefully I'll be able to support my ipod in Ubuntu.

---

### Post by Juzz on 2005-11-03
OK, could be I should try out the Breezy Badger - I am on Hoary Hedgehog...
In my current synaptic with hoary and backports I can't see Banshee anywhere.

---

### Post by Juzz on 2005-11-03
OK, I tried to upgrade to Breezy Badger, but one of the OOo help packages (the one for en_us) held back the entire process :(
But I managed to get synaptic to remove it, since I couldn't do that in the terminal - so in the end I got upgraded.
Now Opera won't run and I can't reinstall it :(
I will have to take a look at opera's hp to see if I can download another version...

---

### Post by Juzz on 2005-11-03
@stuart-newtoubuntu
I had success in encoding to mp4 after upgrading to Breezy Badger, and the faac commandline now has the mp4 options available :)
Now I have to test if it works in my Nokia ;)

You might have to install the gstreamer08-faac and gstreamer08-faad packages (and afterwards running gst-register-0.8 in the terminal).

Things are starting to look up again ;)

---

### Post by riggsd on 2005-11-03
I've never used an AAC or MP4 file, so pardon my ignorance here... my understanding is that these file formats are DRM-capable, which is why iTunes Music Store, etc. use them. iTunes, your iPod, and all other mp3 players are perfectly capable of using mp3. I don't understand why you'd bother to create a non-DRM AAC file when an mp3 would work just the same (while being a more universal format). Can you explain why you seem to be choosing the needlessly-difficult path for encoding your music?

---

### Post by stuart-newtoubuntu on 2005-11-04
Juzz- Are you still using Grip or are you using Banshee? I've started trying to get this working again! I can't resist the challenge. 

I have all the packages installed and I've added the "-w" to my encoder line but I still get a no write access message, after the initail rip to wav. The wav file is perfect though.  

I already use breezy. Do you have any idea what I'm doing wrong?

There are reasons why I am not using mp3, the first is that all my music already exists as mp4 and I like consitency. I'm not willing to re-encode everything. 

As for the DRM, I don't have any files from the itunes music store and I've never enountered a problem with this format. I have had DRM issues in the past with a different format. I owned a Sony Net MD :( and had to use Sony's ridiculous Atarc/atarc3+ formats.

---

### Post by timeoff on 2005-11-04
Stuart,

I got faac through synaptic yesterday, and set up grip to use faac as follows:

in the encoder section of grip

encoder executable: /usr/bin/faac
encoder command line: -w -q 125 --writer %a --artist %A --album %d --title %n --track %t --year %y --genre %G %w
encode file extension: m4a
encode file format: ~/mp3/%A/%d/%t - %n.%x

and it worked straight off.

the -q option can be set to whatever percentage figure you are after.

T

---

### Post by Juzz on 2005-11-06
stuart-newtoubuntu,

I think your main issue would be that you encode to a place outside your home directory, if you try the settings that timeoff wrote - then you might be luckier ;)

---

### Post by sinaen on 2006-03-23
iv'e know that ipod has support for audiobooks but it seems to be in m4a format?

does anyone of you know about m4a? and how you can convert mp3 to m4a?

---

