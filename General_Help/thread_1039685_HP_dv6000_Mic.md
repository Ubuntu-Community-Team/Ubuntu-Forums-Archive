---
title: "HP dv6000 Mic"
date: 2009-01-14
forum: General Help
---

### Post by Prominence on 2009-01-14
Alright, I've been using Ubuntu for over a year now and I've installed it and spread it to countless people but I've come across a problem...I'm really praying it can be fixed, it's the internal microphones, I recently discovered this when I installed Skype. I would really love to have my microphone working for this, I would love to keep in touch with my girlfriend, friends, and family, so please help.

---

### Post by Prominence on 2009-01-15
Bump

---

### Post by tim183 on 2009-03-15
I don't have a solution for you, but I can confirm this problem also affects my HP dv6834eg (dv6000 series) laptop.

Any solutions out there?

---

### Post by tim183 on 2009-03-18
I did hear one solution involving changing also to esound or something like that, does anyone have any information?

---

### Post by LindaLou on 2009-03-18
I found this post from last year.  I could be useful for you. It is for Ubuntu 8.10 and I'm not sure which version you have.  I have the similar issues as you, with Ubuntu 8.04 on my HP Pavilion zx5000.  I can hear the person on the other end when I use say Twinkle or Wengophone but they can't hear me.  Worked fine until a few months ago and I have yet to find a resolve.  Think I will have my jack checked out to see if that is faulty and need replacing.

---

### Post by tim183 on 2009-03-18
I can use an external mic without problems, I ave used bot a a USB phone and a regular 3.5mm headphone and mic set-up on skype before.

However the internal mic ( built-into the laptop near the webcam) don't work. I upgraded to 9.04 Alpha 6 yesterday, and still no recording is possible with the internal microphone.

---

### Post by sananth on 2009-03-24
Prominence and tim183, I have a DV6748 as well, and have been trying for a while to get my microphone working. I have tried countless forum post suggestions, and nothing seems to work. This is the stuff I tried so far:

1. Un-muting all the devices as mentioned on various posts
2. Different versions of Ubuntu (32bit and 64-bit) 7.10, 8.04 and 8.10
3. Bluetooth - I came real close with this one, but still got crashes with Audacity, and never got sound recorder or skype to work
4. I compiled Alsa 1.0.16, 1.0.17 and 1.0.18 from source (based on some bug fixes which people said took care of this issue)
4. I also tried the newer Jaunty Alphas in the hope that something was fixed, but still no avail.

Many people are trying to get this fixed in multiple posts, but they seem to be ignored too. I have been using Ubuntu for ~3 years now (and converted most of my colleagues, friends and relatives), but I have never been able to get the internal microphone working. 

This is the only thing hindering me from totally exorcising the Vista/XP demons that plague my computers.

I added my support to this idea:
[http://brainstorm.ubuntu.com/idea/7050/](http://brainstorm.ubuntu.com/idea/7050/)

Even though someone worded this badly, the message is clear. So, if possible, please rally your support for it by voting for it, and asking your friends to vote for it as well. In the meantime, I shall continue my search, and if I find anything, I will let you know. 

Best of luck! Please PM me if you are able to get this working.

---

### Post by tim183 on 2009-03-24
I voted!!!!

This is such a common notebook model, I can't beleive a fix hasn't been found yet!

---

### Post by sananth on 2009-03-27
Hello all,

 I have some great news to report! I have my mic working! 

After almost totally giving up, I decided to debug the issue myself. So, I went over to alsa-project.org and then started reading up on the documentation about the hda-intel cards and debugging techniques. Here are the steps I followed, and I hope they solve your problems too!

1. Open up a console, and type:

wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
sudo python run.py

2. This will bring up a window with a bunch of debug settings. 

In that window, under "card-0 > codec-0" you will see a couple of devices labeled "AUD_IN". In my case ( DV6748 ) the labels were "Node[0x14]AUD_IN" and "Node[0x15]AUD_IN". Just click on option "Node[0x14]AUD_IN" (it may be different in your case, and you might need to experiment if my steps dont work).

3. The node editor on the right will pop up a "Connection List" with pin complexes. In my case, I had two pin complexes 0x1d and 0x17. I chose 0x17 and would recommend you choose the same (or in a similar circumstance, choose the option that was not chosen by default).

4. Close this window 

5. When asked if you want to revert, click "No"

6. Open up sound-recorder and set the Capture to "Internal Mic" and try recording your voice

If at this point it doesnt work for you, try opening up alsamixer from command line and un-muting your mic sources and mic-boost. If you want me to explain that, let me know.

Prominence & tim183, let me know if this works for you. If it does, spread the word! :D

---

### Post by spcwingo on 2009-03-30
> **sananth said:**
> Hello all,

 I have some great news to report! I have my mic working! 

After almost totally giving up, I decided to debug the issue myself. So, I went over to alsa-project.org and then started reading up on the documentation about the hda-intel cards and debugging techniques. Here are the steps I followed, and I hope they solve your problems too!

1. Open up a console, and type:

wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
python run.py

2. This will bring up a window with a bunch of debug settings. 

In that window, under "card-0 > codec-0" you will see a couple of devices labeled "AUD_IN". In my case ( DV6748 ) the labels were "Node[0x14]AUD_IN" and "Node[0x15]AUD_IN". Just click on option "Node[0x14]AUD_IN" (it may be different in your case, and you might need to experiment if my steps dont work).

3. The node editor on the right will pop up a "Connection List" with pin complexes. In my case, I had two pin complexes 0x1d and 0x17. I chose 0x17 and would recommend you choose the same (or in a similar circumstance, choose the option that was not chosen by default).

4. Close this window 

5. When asked if you want to revert, click "No"

6. Open up sound-recorder and set the Capture to "Internal Mic" and try recording your voice

If at this point it doesnt work for you, try opening up alsamixer from command line and un-muting your mic sources and mic-boost. If you want me to explain that, let me know.

Prominence & tim183, let me know if this works for you. If it does, spread the word! :D

My wife thanks you, and so do I.  I swear, I was pulling my hair out over this one.  Your solution was quick and painless.  Thanks again.

EDIT: After reboot it resets itself.  Do you know of any way to make the settings stick?

---

### Post by sananth on 2009-04-03
> **spcwingo said:**
> My wife thanks you, and so do I.  I swear, I was pulling my hair out over this one.  Your solution was quick and painless.  Thanks again.

EDIT: After reboot it resets itself.  Do you know of any way to make the settings stick?

Glad I could help! I already lost a lot of hair to this one! 

My settings seem to stick ... not really sure why you are not able to see this. I will check my alsa config and let you know if there is some way to make it permanent for you too.

BTW, which version of ALSA are you running? I am on 1.0.18.

---

### Post by tim183 on 2009-04-04
here is the output I get, am I doing something wrong?

I#m on ubuntu jaunty 64 bit


tim@tim:~$ 
tim@tim:~$ wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
--2009-04-04 16:13:44--  [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa.git;a=blob_plain;f=hda-analyzer/run.py](http://git.alsa-project.org/?p=alsa.git;a=blob_plain;f=hda-analyzer/run.py) [following]
--2009-04-04 16:13:45--  [http://git.alsa-project.org/?p=alsa.git;a=blob_plain;f=hda-analyzer/run.py](http://git.alsa-project.org/?p=alsa.git;a=blob_plain;f=hda-analyzer/run.py)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `run.py'

    [ <=>                                   ] 892         --.-K/s   in 0s      

2009-04-04 16:13:45 (57.5 MB/s) - `run.py' saved [892]

tim@tim:~$ python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.
tim@tim:~$ sudo python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.
tim@tim:~$

---

### Post by Dawei87 on 2009-04-04
I get the same errors as above post in jaunty 32bit..

---

### Post by tim183 on 2009-04-04
I'm definately not an expert but i believe it's something to do with the errors currently in python in Jaunty

---

### Post by sananth on 2009-04-04
tim183, how did you install alsa? Was it from source or was it just the regular installation? I would recommend installing from this thread:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

I think this should help with the executing the python script. Also do 
ls -l /dev/snd/controlC*
ls -l /dev/snd/hwdepC*D* 

and check if you have those devices. My guess is that you will not see them if you did not use the alsa script. 

Dawei87, I am running 8.10 64-bit on my machine, but I can try 9.04 32-bit through live cd/usb and let you know what I get.

---

### Post by sananth on 2009-04-07
spcwingo, I was able to make the settings stick by writing a python script that made use of hda_codec.py and hda_codec.pyc which are files downloaded when you run hda analyzer. I am attaching the required files here. Simply download them, and throw them into /etc/init.d/. Once you do so, make test_hda.py executable like this:

sudo chmod +x ./test_hda.py

Then, run the following command to kick off test_hda.py every time you boot up:

sudo update-rc.d test_hda.py defaults

WARNING: test_hda.py was only designed to work for the HP laptop DV6748. For other laptops, please find your card number (0,1,2 etc.), codec number (0,1,2,3, etc), mic node number from hda analyzer as an INTEGER (hda analyzer shows the node's hex number which you will need to convert to an integer) and also the row number for the pin you want to switch your default to (0,1,2 etc.). Feel free to edit test_hda.py to add all this information, and then try running it as root to see if the desired effect is achieved. This code should only be used to make your settings stick if you got your mic working using hda analyzer from alsa-project.org.

---

### Post by tim183 on 2009-04-08
> **sananth said:**
> tim183, how did you install alsa? Was it from source or was it just the regular installation? I would recommend installing from this thread:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

I think this should help with the executing the python script. Also do 
ls -l /dev/snd/controlC*
ls -l /dev/snd/hwdepC*D* 

and check if you have those devices. My guess is that you will not see them if you did not use the alsa script. 

Dawei87, I am running 8.10 64-bit on my machine, but I can try 9.04 32-bit through live cd/usb and let you know what I get.

tim@tim:~$ ls -l /dev/snd/controlC*
crw-rw----+ 1 root audio 116, 7 2009-04-06 23:52 /dev/snd/controlC0
tim@tim:~$ ls -l /dev/snd/hwdepC*D* 
ls: cannot access /dev/snd/hwdepC*D*: No such file or directory
tim@tim:~$

---

### Post by sananth on 2009-04-09
tim183, I was able to see this from the Jaunty live cd. Did you try to install alsa using the scripts mentioned on the forum link I sent you? If not, please try it out and let me know whether that helps. 

In the meantime, I am going to look into hda analyzer and figure out why this is happening. I will keep you posted.

---

### Post by tim183 on 2009-04-09
Sananth, ok, I will try today

thanks

---

### Post by spcwingo on 2009-04-17
Sorry I'm just now getting back to you.  Just thought I would let you know, sananth, you're my new hero.  That worked like a charm on this dv6707us.  The wifey says thanks too.

---

### Post by nighthawk117 on 2009-04-19
sananth, I tried what you said on my HP dv6000 and I get:

```
root@ktech-laptop:/home/ktech# python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
Traceback (most recent call last):
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 906, in <module>
    main()
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 893, in main
    if read_nodes() == 0:
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 46, in read_nodes
    read_nodes2(c.card, i)
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 36, in read_nodes2
    c.analyze()
  File "/dev/shm/hda-analyzer/hda_codec.py", line 821, in analyze
    pcm = self.param_read(self.afg, PARAMS['PCM'])
  File "/dev/shm/hda-analyzer/hda_codec.py", line 745, in param_read
    return self.rw(nid, VERBS['PARAMETERS'], param)
  File "/dev/shm/hda-analyzer/hda_codec.py", line 730, in rw
    verb = (nid << 24) | (verb << 8) | param
TypeError: unsupported operand type(s) for <<: 'NoneType' and 'int'
```

can you help me out here please?

---

### Post by sananth on 2009-04-20
This looks like it could be a python issue. Which version of python are you running? Use:

python --version 

and post your result. I am using 2.5.2 and it works fine in that version. It looks like python is not able to recognize the bit shift operator here.

Edit:
Could you please run:
sudo python run.py

I also did a quick google search. If running with sudo does not work, also check if you have gcc installed. If not, you might need to install gcc.

---

### Post by tim183 on 2009-04-22
tim@tim:~$ python --version 
Python 2.6.2
tim@tim:~$ 


still doesnt work

---

### Post by Prominence on 2009-04-30
No luck either, same python issue

---

### Post by sananth on 2009-04-30
> **Prominence said:**
> No luck either, same python issue

Everyone, I am currently in the process of upgrading my machines to 9.04. I did see this same issue when I used the 9.04 live CD on my machine. I will post detailed steps once I get this working. I will try to make sure that the steps work for 32-bit and 64-bit. Stay tuned!

---

### Post by Dr.Vista on 2009-05-02
I'm having a similar problem. I have a HP Pavilion dv6700se Notebook with an internal audio. I can hear but I cant record stuff. Here is my capture devices.

> **** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by sananth on 2009-05-03
This set of instructions is for anyone who was unable to run "sudo python run.py" from my previous set of instructions. This new set of instructions is to get a debug version of ALSA installed on your system so that you can use my previous instructions to run HDA analyzer. Please read the instructions carefully, and let me know if you have any questions.

Steps:

1. Open a terminal and run:

which gcc
 
If the output is "/usr/bin/gcc" or something similar, you are set for the installation. If NOT, run the command: 

sudo apt-get install gcc 

and complete the installation of gcc.

2. Download the file called "AlsaUpgrade-1.0.x-rev-1.16.sh" (attached to this post), and put it in your home directory. 

This is the shell script which is going to install ALSA 1.0.19 in debug mode to help us fix our mic settings. Credit for this installer goes to soundcheck and the other good folks at:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

3. Open up a terminal, type:

cd ~
chmod +x ./AlsaUpgrade-1.0.x-rev-1.16.sh
sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di

Now comes the interesting part. This installation will take around 15 minutes, so please be patient. If you would like to follow the progress of the installation, look at the instructions the installation script shows, open up a new terminal, and type:

tail -f /var/log/AlsaUpgradeRev*.log

It is not mandatory to follow the installation. Once the installer is done, you will be able to see the prompt in the terminal to confirm it.

4. Follow the instructions from my previous post in the first page of this thread starting with:

wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
sudo python run.py

This set of instructions should work on most Ubuntu flavors, and on 32-bit and 64-bit systems. If you run into any issues, please let me know.

Best of Luck!

---

### Post by magli on 2009-05-06
> **sananth said:**
> sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh 

You need to add "-di" to the above command to download/install, like this:

```
sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di
```

My upgrade is now in progress. Thanks Sananth.

---

### Post by sananth on 2009-05-06
Thanks magli! I have updated my instructions to use the -di flag (download, install).

---

### Post by Prominence on 2009-05-06
Still no luck, same as before 

grayson@iGrayson:~$ sudo python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.
grayson@iGrayson:~$

---

### Post by sananth on 2009-05-06
> **Prominence said:**
> Still no luck, same as before 

grayson@iGrayson:~$ sudo python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.
grayson@iGrayson:~$

Can you please reboot and try "sudo python run.py" again?

---

### Post by Prominence on 2009-05-06
Ok did so 

grayson@iGrayson:~$ sudo python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
Traceback (most recent call last):
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 906, in <module>
    main()
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 893, in main
    if read_nodes() == 0:
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 46, in read_nodes
    read_nodes2(c.card, i)
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 36, in read_nodes2
    c.analyze()
  File "/dev/shm/hda-analyzer/hda_codec.py", line 821, in analyze
    pcm = self.param_read(self.afg, PARAMS['PCM'])
  File "/dev/shm/hda-analyzer/hda_codec.py", line 745, in param_read
    return self.rw(nid, VERBS['PARAMETERS'], param)
  File "/dev/shm/hda-analyzer/hda_codec.py", line 730, in rw
    verb = (nid << 24) | (verb << 8) | param
TypeError: unsupported operand type(s) for <<: 'NoneType' and 'int'
grayson@iGrayson:~$

---

### Post by sananth on 2009-05-06
> **Prominence said:**
> Ok did so 

grayson@iGrayson:~$ sudo python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
Traceback (most recent call last):
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 906, in <module>
    main()
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 893, in main
    if read_nodes() == 0:
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 46, in read_nodes
    read_nodes2(c.card, i)
  File "/dev/shm/hda-analyzer/hda_analyzer.py", line 36, in read_nodes2
    c.analyze()
  File "/dev/shm/hda-analyzer/hda_codec.py", line 821, in analyze
    pcm = self.param_read(self.afg, PARAMS['PCM'])
  File "/dev/shm/hda-analyzer/hda_codec.py", line 745, in param_read
    return self.rw(nid, VERBS['PARAMETERS'], param)
  File "/dev/shm/hda-analyzer/hda_codec.py", line 730, in rw
    verb = (nid << 24) | (verb << 8) | param
TypeError: unsupported operand type(s) for <<: 'NoneType' and 'int'
grayson@iGrayson:~$

Prominence, I have a fix for you:

1. Download the zip from this post and unzip its contents to your home directory.

2. Open up a terminal and type:

sudo cp ~/hda_codec.py /dev/shm/hda-analyzer/
cd /dev/shm/hda-analyzer
sudo python ./hda_analyzer.py

This should bring up the HDA analyzer dialog correctly. I know some other people also ran into these issues, so please let me know if this fix helps. I have modified hda_codec.py to add a small null check to prevent that abort.

---

### Post by Prominence on 2009-05-06
Once you get to the nodes you lose me completely

---

### Post by sananth on 2009-05-06
So were you able to get to the nodes? 

If yes, all you have to do is look for the nodes with the [AUD_IN] label next to them. These represent audio capture devices. 

Now if you click on those nodes, the right side of the window is going to change. Just look around for the keyword "pin". You will find a place with a couple of radio buttons. Just change the radio button from one option to another. Then try using the sound recorder application to test your microphone.

The main problem with HP notebooks like ours and the HDA ALSA driver is that our pin configuration is messed up in the driver. We need to play around with the configuration, then test the recording with "Sound Recorder" or other sound applications till we figure out the right pin configurations. In fact, it would be very helpful everyone could state their exact HP laptop model number, and also their pin configuration changes. This would help other people who read these posts, and are looking for a microphone fix.

Does this make sense?

---

### Post by Prominence on 2009-05-06
Well, it works in Skype now, it's choppy as hell in the recorder, but fine in Skype.

---

### Post by dharmahound on 2009-05-09
Hey Sananth,

Your scripts have gotten my mic working when nothing else would -- thank you so much!!

I have the same problem that someone else did though, the settings don't stick when I reboot.  I tried using the script that you gave in response to that problem, which seemed to work for the other guy, but it doesn't do much for me.  I'm on a Pavillion dv6815nr, seems pretty similar to the 66 and 67 series that worked for other people, so I'm not sure what the problem could be.  

Is there any information I could give you that would help clarify my situation?  I'm pretty new to linux.

Thank you again!
With gratitude,
Andrew

---

### Post by hero1900 on 2009-05-22
thanks to all of you
but i have a small problem
when i click on any of AUD-in NODE it gave me only one option button in the connection list, any one can help

---

### Post by Potters Son on 2009-05-31
Ditto hero1900.

I have a dv6985se, and I think I remember the built-in mikes working in Hardy, which depresses me (I don't want to downgrade). The problem with my laptop, as far as I could tell before reading this post, was that ALSA doesn't seem to know that the mikes exist. (I say mikes in the plural because there are two on either side of the webcam to form a stereo microphone... I don't know if that complicates my problem.) I base this assumption on what I see in Audacity. For the sound output, Audacity lists "ALSA: HDA Intel: ALC268 Analog (hw:0,0)", "ALSA: front", "ALSA: surround40", "ALSA: surround51", "ALSA: surround71", "ALSA: default", "ALSA: dmix", and "OSS: /dev/dsp". But for input, Audacity only has "ALSA: HDA Intel: ALC268 Analog (hw:0,0)", "ALSA: default", and "OSS: /dev/dsp". In addition to these, I remember it listing "ALSA: front" as a microphone.

Well, I got through all the steps (thankfully), but I have no clue what to do next. The nodes labeled "AUD_IN" only have one radio button each in their "Connection List" boxes, and all the "PIN"s either have one radio button or none at all.

Should I give you the output of some configuration file or something?

[edit:]

Okay, I figured out what you mean. The various nodes pipe the signal between themselves.
There are two sound input nodes: Node[0x07] AUD_IN and Node[0x08] AUD_IN. These connect to Node[0x23] AUD_SEL and Node[0x24] AUD_SEL respectively. From here, these nodes both connected to Node[0x18] PIN. Herin lay the error. In the Config Default box of Node[0x18], the pin is labeled as exterior: "Jack location: Ext". Node[0x19], by contrast, is labeled interior. Because both AUD_SEL's were trying to connect to the same node, they were colliding. I'm guessing that the exterior mike won out over the interior one because when you connect a pair of headphones to the computer, the built-in speakers are automatically muted. I think the microphone was trying to do the same thing, except something in the computer thought a microphone was connected whether or not a mike was actually connected. To remedy this, I set Node[0x23] to connect to Pin Complex [0x19].

The effect was this: The internal mike was operational, but the external wasn't. I put the computer in sleep mode and took it back out, and the external mike worked but the internal mike didn't. I restarted HDAAnalyzer and changed the settings again, and the internal one worked again. This could get annoying.

Sorry about the lengthly writeup.

---

### Post by rotnacogeid on 2009-06-09
I downloaded the script to update alsa and at the end of the log file this is what it appears:
[HTML]
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) wer
e not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

alsa-plugins-1.0.19 configure failed
[/HTML]

When I run "sudo python run.py" it failed like this:

[HTML]
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.

[/HTML]

I appreciate any help

---

### Post by marksz on 2009-06-22
Thank you so much!  Changing that pin 1d to 17 got my microphone working after running both your scripts (AlsaUpgrade-1.0.x-rev-1.16.sh and run.py)  on my HP Pavilion dv9715nr.  This is a fairly hard to find solution for what appears to be a common problem with many HP laptops.  I hope it will be fixed in the next release.  Thanks again for posting scripts to make the fix easy!!!

---

### Post by over_my_head on 2009-06-26
Hi there,
sanath - thank you so much for posting this. i was definitely getting to the tearing-out-hair point when i found this and now i can hear myself on the sound recorder... when i got into the nodes it appeared that both mics were muted. don't know if that info will help anyone else but definitely check the 'mute' boxes when you're looking at the pin configs. i attached a screeen shot of the hda analyzer with boxes i'm talking about indicated with a red arrow. couldn't figure out an easy way of putting the image in the message. anyway, thanks again!
i'm off to test skype!!

---

### Post by over_my_head on 2009-06-28
ok, so i got skype working!! woohoo!
one thing i noticed - i had to go into the options on skype and uncheck the box that said something like 'allow skype to automatically set your sound mixers' because otherwise it was automatically turning OFF my mics.
took me a while to figure that out so i thought i'd mention it in case anyone else has the same problem.:D

---

### Post by YasirMX on 2009-07-21
> **sananth said:**
> Hello all,

 I have some great news to report! I have my mic working! 

After almost totally giving up, I decided to debug the issue myself. So, I went over to alsa-project.org and then started reading up on the documentation about the hda-intel cards and debugging techniques. Here are the steps I followed, and I hope they solve your problems too!

1. Open up a console, and type:

wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
sudo python run.py

2. This will bring up a window with a bunch of debug settings. 

In that window, under "card-0 > codec-0" you will see a couple of devices labeled "AUD_IN". In my case ( DV6748 ) the labels were "Node[0x14]AUD_IN" and "Node[0x15]AUD_IN". Just click on option "Node[0x14]AUD_IN" (it may be different in your case, and you might need to experiment if my steps dont work).

3. The node editor on the right will pop up a "Connection List" with pin complexes. In my case, I had two pin complexes 0x1d and 0x17. I chose 0x17 and would recommend you choose the same (or in a similar circumstance, choose the option that was not chosen by default).

4. Close this window 

5. When asked if you want to revert, click "No"

6. Open up sound-recorder and set the Capture to "Internal Mic" and try recording your voice

If at this point it doesnt work for you, try opening up alsamixer from command line and un-muting your mic sources and mic-boost. If you want me to explain that, let me know.

Prominence & tim183, let me know if this works for you. If it does, spread the word! :D

I've run your terminal command and got this:

```

root@YasirMX:/home/yasir# python run2.py
No protocol specified
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No protocol specified
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
No HDA codecs were found or insufficient priviledges for
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.


```

---

### Post by sananth on 2009-07-21
YasirMX, please look at my post #27 in this same thread to fix this issue.

Here is the link:

[http://ubuntuforums.org/showpost.php?p=7206043&postcount=27]("http://ubuntuforums.org/showpost.php?p=7206043&postcount=27")

I have been a bit lazy lately, but I think I need to bring up this issue with the good folks at ALSA, so that they can put in a fix/option for people like us.

I also realize that my posts are buried somewhere in this thread, so I will try to consolidate them, and create a new thread as a tutorial for this issue.

---

### Post by sananth on 2009-07-21
> **rotnacogeid said:**
> I downloaded the script to update alsa and at the end of the log file this is what it appears:
[HTML]
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) wer
e not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

alsa-plugins-1.0.19 configure failed
[/HTML]

When I run "sudo python run.py" it failed like this:

[HTML]
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.

[/HTML]

I appreciate any help

From this post:
[http://ubuntuforums.org/showpost.php?p=6025202&postcount=149]("http://ubuntuforums.org/showpost.php?p=6025202&postcount=149")

it looks like you might need to install libasound2-dev

Simply open up Synaptic Package Manager, search for libasound2-dev. Install it, and then re-try my steps.

---

### Post by YasirMX on 2009-07-23
> **sananth said:**
> YasirMX, please look at my post #27 in this same thread to fix this issue.

Here is the link:

[http://ubuntuforums.org/showpost.php?p=7206043&postcount=27](http://ubuntuforums.org/showpost.php?p=7206043&postcount=27)

I have been a bit lazy lately, but I think I need to bring up this issue with the good folks at ALSA, so that they can put in a fix/option for people like us.

I also realize that my posts are buried somewhere in this thread, so I will try to consolidate them, and create a new thread as a tutorial for this issue.

Thanks for your suggestion it seems I'm still running into some difficulties. I followed all your steps as mentioned.. I've been able to bring up the HDA debug window and selected AUD_IN 14 and 15 as well but wihout success..the the .py scripts have executed properly but when I run Sound Recorder, it tells me:
"Your Audio capture settings are invalid, Please correct them with the sound preferences..."

Any suggestions?? By the way, I download latest ALSA driver and built them.. I'm pavilion DV6820ea

Thanks again for participating and helping me out :)

---

### Post by sananth on 2009-07-23
> **YasirMX said:**
> Thanks for your suggestion it seems I'm still running into some difficulties. I followed all your steps as mentioned.. I've been able to bring up the HDA debug window and selected AUD_IN 14 and 15 as well but wihout success..the the .py scripts have executed properly but when I run Sound Recorder, it tells me:
"Your Audio capture settings are invalid, Please correct them with the sound preferences..."

Any suggestions?? By the way, I download latest ALSA driver and built them.. I'm pavilion DV6820ea

Thanks again for participating and helping me out :)

YasirMX, could you please take a screenshot of your the HDA debug window and post it here? What do you mean by "selected AUD_IN 14 and 15" ? You will first have to click on 14, and then change the pin complex shown on the right hand side of the same window. Did you do that?

Even if you did all this correctly, you may still have to go to "System->Preferences->Sound" and make sure that your input is set to ALSA, and not Pulseaudio, or some other option.

---

### Post by Potters Son on 2009-08-19
I apologize in advance for the flame; I'm just so tired and frustrated with this microphone.

I followed these directions the other day and got the microphone set up correctly. However, when I installed Skype today, I couldn't get the microphone to pick up any sound. I went into Audacity (my primary acid test for whether my microphone is working correctly), and that didn't pick up anything either. Finally, I went to /dev/shm, where the Python scripts get installed to, and found that the ALSA upgrade was gone! UBUNTU OVERWROTE MY ALSA UPGRADE, AND NOW I HAVE TO START ALL OVER AGAIN FROM THE BEGINNING! THAT MEANS ANOTHER TWENTY MINUTES OF MY LIFE IS NOW WASTED ON THIS STUPID INTERNAL MICROPHONE!!!

</yelling>

*Breathe*

Is there any way to get these settings (or the ALSA upgrade) to stick? Or, has anyone made a PGP package so I don't have to spend all that time watching AlsaUpgrade_*** doing who knows what?

Moreover, I would like to ask if any headway is being made toward fixing the microphones in the first place? I mean, with Hardy Heron, there was an option in Audacity called "ALSA: front", and that always worked. Now, it's completely gone. Even when I change the pin configuration under HDA_Analyzer, I sacrifice the microphone jack in order to have the internal one. This is a major regression, and it makes me consider downgrading.

Thank you for your patience, and I hope that I haven't upset or offended anyone.

---

