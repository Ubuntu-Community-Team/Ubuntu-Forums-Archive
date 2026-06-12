---
title: "Can't upgrade to 10.04...? Mini 10v"
date: 2010-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nickxm on 2010-05-01
So as stated I am using a Dell Mini 10v, which is currently on the 8.04 LTS and I expected to be able to upgrade to the next LTS and I follow their directions with the update-manager but it fails to bring up the screen saying that I am able to update to 10.04?

Any thoughts/ideas? :(
I would love to get on 10.04~:(

---

### Post by hedgeborn on 2010-05-01
I have a Dell Latitude 2100, which I think is a close cousin to the Mini 10 and I was able to do it by using a bootable USB dongle.

I downloaded the ISO and then used Startup Disk Creator to make a bootable USB drive. You can then restart your machine with the USB drive connected and hit ESC to interupt the boot process and get it to boot from the USB drive and run the installer from there.

NOTE: I'm a newbie myself, so there are other people here who are far more qualified to guide you on this, but this process worked for me (updated from Dellbuntu 8.10 to 10.4 netbook version)

Whatever you do, back everything up beforehand! 

I decided to reformat my drive to get rid of all the little extra partitions and stuff and have a fresh start. 

For what it's worth though, I'm pretty sure the Dell Mini 10's are very very similar hardware wise to my netbook and 10.4 runs beautifully on my machine so I'm sure you can do it.

---

### Post by Nickxm on 2010-05-01
Thanks Hedgeborn~ I will probably give it a go tonight or tomorrow morning if someone can't answer why it doesn't work via the Update-Manager. :)

---

### Post by ugm6hr on 2010-05-02
If you have the Dell original 8.04LTS, you will only be able to upgrade when (? if) Dell supports it.

I think you are better off re-installing, since support or the Atom-specific lpia kernel has been dropped (I think) - so unless Dell pushes for it, you may be waiting a while....

---

### Post by sanderella on 2010-05-02
:? Similar problems.Never had any problems upgrading/installin before.

I have an Inspiron 1300. When I try to boot from disc (by pressing F12), the loading screen for 09:10 comes onto the screen and this old version boots from the hard disc. I tried pressing esc and delete, but it doesn't work. Any ideas folks? Thanks.

---

### Post by ugm6hr on 2010-05-02
> **sanderella said:**
> :? Similar problems.Never had any problems upgrading/installin before.

I have an Inspiron 1300. When I try to boot from disc (by pressing F12), the loading screen for 09:10 comes onto the screen and this old version boots from the hard disc. I tried pressing esc and delete, but it doesn't work. Any ideas folks? Thanks.

Please start a different thread for help.

---

### Post by snowpine on 2010-05-02
Please post the output of:

```
uname -a
```

If your kernel is of the "lpia" architecture, your only upgrade option is: back up personal documents, install 10.04, restore documents from backup.

---

### Post by bri5569 on 2010-05-02
My I suggest you back up your Fluendo codecs before you do anything. I have been testing 10.04 on my mini 10v for sometime and could find nothing that would play all media so before I installed it I saved my fluendo codecs and then installed them when I installed a fresh install of 10.04. It is definitively worth the time switching from Dell's 8.04 just to get away from LPIA and my battery life is much better now but as I say back up your codecs first - they are about $30 to buy!

---

### Post by Nickxm on 2010-05-02
> **snowpine said:**
> Please post the output of:

```
uname -a
```If your kernel is of the "lpia" architecture, your only upgrade option is: back up personal documents, install 10.04, restore documents from backup.

lpia #1 SMP Wed Feb 17 22:14:54 UTC 2010 i686 GNU/Linux

lpia it is... So I guess I should just copy over some files and get working on the USB bootkey, lol. I appreciate everyones support on this. Gotta love the Ubuntu community. Informative and very friendly. :)

Kind of a open ended question more based off of what @bri5569 said.
How would I go about copying my Fluendo codecs? :)
I will start searching to see if theres a thread for it also.

Oh and last question would be... Install Netbook remix 10.04, yes? :)

Thank you all! :D:popcorn:

---

### Post by ugm6hr on 2010-05-03
If you like the Netbook Remix interface - then yes - 10.04 Netbook Remix.

I didn't backup my codecs.... so don't know how to do that.

---

### Post by Nickxm on 2010-05-03
> **ugm6hr said:**
> If you like the Netbook Remix interface - then yes - 10.04 Netbook Remix.

I didn't backup my codecs.... so don't know how to do that.
I decided not to do the backup on my codecs either, lol.

I am attempting to install now but am running into some minor problems.
I am using Unetbootin and when I select which 10.04 I am installing, do I pick 10.04_Live? 10.04_NetInstall? x.x; ...This is my first time doing something serious on Ubuntu, I am really curious to what I should do here...

Just experimenting I have decided to try to use NetInstall since it seems logical since I am using the netbook remix iso? ...After what do I do exactly? Nothing really happens and if I take out my USB drive the netbook freaks out on me, lol...

I am trying to find guides somewhere for installing 10.04 on a mini 10v but am coming up short handed.

---

### Post by Nickxm on 2010-05-03
I think I have figured it out kind of, finally. Lol... The damn layout confused me some and being a newbie to Ubuntu... Lil tricky.

The HDD Icon in the top left hand side is a key feature that should be made aware of. After you start from USB Drive, run the install that shows up on the "desktop screen" - Answer the 7 questions to set yourself up and then click Install. After which, click that little HDD icon in the top left beside the Ubuntu logo and let it install the system... :popcorn:

If anything important happens after which that is confusing to me I'll post and update what I did as well. :x 

...No more installing things at 1AM for me. hah
--

Okay so there was one problem that has come up!
After it installed and I restarted as it stated too, a screen came up before going to the login that there was an errors, it couldn't find a few things... Went away too quick for me to be able to actually record them. ><; Anyone know what's going on here?

---

### Post by bri5569 on 2010-05-03
To save your Fluendo codecs in Dell's Ubuntu 8.04 
1 - go to filesystem, then usr, then lib, then gstreamer0.10
2 - copy all files that start with libgstflu - I think there are 14 in total and save them to a usb drive.
3 - when you have installed 10.04 (i preferred the desktop version and deleted the bottom panel) go to filesystem, usr, and gstreamer-0.10(note the hypen) and paste your codecs from Fluendo in there.

The sound is much better with these and all media files will play.

There is probably an easier way to do this but this worked for me.

---

### Post by Nickxm on 2010-05-03
I am getting ready to install the desktop LTS version of Lucid now to see how I like it. Netbook remix is kind of ..Too different compared to what I am use too with 8.04 lol.

---

### Post by snowpine on 2010-05-03
Good Ubuntu how-to's for the Dell Mini 10v here: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by teejayuu on 2010-05-06
> **bri5569 said:**
> To save your Fluendo codecs in Dell's Ubuntu 8.04 
1 - go to filesystem, then usr, then lib, then gstreamer0.10
2 - copy all files that start with libgstflu - I think there are 14 in total and save them to a usb drive.
3 - when you have installed 10.04 (i preferred the desktop version and deleted the bottom panel) go to filesystem, usr, and gstreamer-0.10(note the hypen) and paste your codecs from Fluendo in there.
 
The sound is much better with these and all media files will play.
 
There is probably an easier way to do this but this worked for me.
 
I'm a Linux newbie. I have a Dell mini 10 that came with ubuntu 8.04. I have today installed Lucid Lynx and am trying to paste fluendo codecs to /usr/lib/gsteamer-0.10 and the paste command, amongst others, is disabled. I think this is down to permissions, is there any way to override this?

---

### Post by bri5569 on 2010-05-06
copy your Fluendo codecs that you saved from 8.04 to a folder named codecs on your desktop of 10.04

then in terminal type

sudo cp ./codecs/* /usr/lib/gstreamer-0.10/

Come back to me if this doesn't work

---

### Post by bri5569 on 2010-05-06
to test that your codecs have copied over type in terminal

gst-inspect-0.10 | grep flu

which should show the following result 

flumpeg4vdec:  flumpeg4vdec: Fluendo MPEG-4 ASP Video Decoder
flurtp:  flurtpasfdepay: RTP packet parser
fludivx3dec:  fludivx3dec: Fluendo DivX 3.11 Decoder
fluwmvdec:  fluwmvdec: Fluendo WMV Decoder
fluisodemux:  fluisodemux: ISODemux Demuxer
fluaacdec:  fluaacdec: Fluendo AAC Decoder
flumpegdemux:  flutsdemux: MPEG Transport stream demuxer
flumpegdemux:  flupsdemux: MPEG Program Demuxer
flumms:  flummssrc: Fluendo MMS source
fluasf:  fluasfcmdparse: Fluendo ASF Command Parser
fluasf:  fluasfdemux: Fluendo ASF Demuxer
flumpeg2vdec:  flumpeg2vdec: Fluendo MPEG-2 Video Decoder
flump3dec:  flump3dec: Fluendo MP3 Decoder (IPP build)
fluh264dec:  fluh264dec: Fluendo H264 Decoder
flulpcm:  flulpcmdec: Fluendo LPCM decoder

---

### Post by teejayuu on 2010-05-08
Hi Bri

I have tried *sudo cp ./codecs/* /usr/lib/gstreamer-0.10/* (had to *cd Desktop* first) but I am getting the message:
cp: omittng directory './codecs/usr'

What am I doing wrong?

Edit: Ignore - the files were in ./codecs/usr/lib/gstreamer-0.10.  Moved them to ./codecs and all worked as you said. 

Thanks
Tony

---

### Post by bri5569 on 2010-05-09
hi teejayuu

glad to hear everything is working ok. These codecs work well with 10.04LTS and since you have to buy them I believe it is worth while saving them from Dells version of 8.04. I couldn't get wma files to work without them so I found it worthwhile reloading dell's version just to get them.

I'm a newbie myself but this forum will keep you right if you have any problems. Some of the ones on here must be ubuntu mad and I'm glad they are. I'll never go back to windows now.

Bri

---

### Post by shiningkenmonster on 2010-05-11
you don't need to install Fluendo codecs.

Upon installing a new version of Ubuntu. You need to install 

Medibuntu 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and install:
ubuntu-restricted-extra
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

in the terminal you type in:
```
sudo apt-get install ubuntu-restricted-extras

```

upon installing everything. if you want to install adobe reader, skype and/or java. and everything else.

you can install vlc. vlc will play almost all the restricted formats. such as movies and such. you can install it on the terminal:
```
sudo apt-get install vlc
```

---

### Post by bri5569 on 2010-05-12
I had tried this when testing 10.04RC and still couldn't get some of my wma files to play. Most 10v owners who bought their netbook with Ubuntu installed have paid for the Fluendo codecs so why not use them. I find my audio is much better with these than any other.

Anyone who didn't get the Dell's version of 8.04LTS would certainly need to go down the path you mentioned.

---

### Post by engr_sav on 2010-06-03
tried this but access is denied to the gstreamer-0.10 folder, cant get the files copied over. any suggestions? thanks

---

### Post by ugm6hr on 2010-06-03
> **engr_sav said:**
> tried this but access is denied to the gstreamer-0.10 folder, cant get the files copied over. any suggestions? thanks

Use:
```
gksudo nautilus
```

Or
[http://ubuntuforums.org/showpost.php?p=9250938&postcount=17](http://ubuntuforums.org/showpost.php?p=9250938&postcount=17)

What's sudo? [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

