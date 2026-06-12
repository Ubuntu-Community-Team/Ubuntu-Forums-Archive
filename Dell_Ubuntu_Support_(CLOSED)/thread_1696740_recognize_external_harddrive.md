---
title: "recognize external harddrive"
date: 2011-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by steffani on 2011-02-27
hello i have a dell with ubuntu hardy heron (that an ex put on for me) I do not know so much  about computers but use it quite alot......this afternoon while trying to update my gimp...i kinda aciidently (thinking it was no big deal) updated my whole program to lucid lynx...i have an external hard drive to protect all my "stuff" and now it does nt read it ...nor does it even recognize it ...the other problem is i cant seem to find how to shut down its all so different .... i really hope i did nt mess up too big and hope even more that there is some awesome "geek" ( and i mean that as a complement) out there who can help me out in vocabulary that i can actually understand ..thanks xo steff:KS

---

### Post by myth1914 on 2011-02-27
After the upgrade, have you run an update to be sure you're current?

---

### Post by steffani on 2011-02-27
no i guess not.....it just took over and said done........when it was done....you think that might help..

---

### Post by myth1914 on 2011-02-27
I don't know that it will completely resolve the issues, but as you updated from the last LTS release to the current, it's sure to have quite a few updates not included in the install.  (Although it's been quite some time since I've done so)  In any case, run

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by steffani on 2011-02-27
okay right ...but how exactly do i "run" something......sorry for being such a dork.....

---

### Post by myth1914 on 2011-02-27
Once done, post the output of ```
lsusb
``` with the external drive plugged in please.

---

### Post by myth1914 on 2011-02-27
> **steffani said:**
> okay right ...but how exactly do i "run" something......sorry for being such a dork.....

If you're running Gnome, it will be under Applications -> Accessories -> Terminal

Launch the terminal and copy/paste that in.  Hit enter and it will ask for your sudo password (the same as what was needed to upgrade the last time)  Once finished, type ```
clear
``` into the terminal, hit enter, followed by ```
lsusb
```.  Hit enter, this should list all devices plugged into the USB ports.  Copy the entire output and paste it into your reply.

---

### Post by steffani on 2011-02-27
oh my .....sorry you really lost me ...could you please walk me through this in more detail  i really have no idea...where to go to even "run" anything.........

---

### Post by steffani on 2011-02-27
okay so done but it says not found

---

### Post by myth1914 on 2011-02-27
OK, that just means it's up to date.  Now, from the same terminal, copy the output of lsusb and post it in your next reply.

---

### Post by steffani on 2011-02-27
what came up after i wrote in lsusb was...
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
  and then not found ect ect......any ideas?

---

### Post by SeijiSensei on 2011-02-27
Start with this:  [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Follow the instructions to open a "terminal."  You'll see a window open on the screen with a "prompt" that looks something like this:

```
steffani@localhost:~$
```

Type the command myth1914 gave you after the dollar-sign:

```
sudo apt-get update && sudo apt-get upgrade
```

Hit the enter key.  You'll be asked to enter your password.  It's the one you always use to log in.  Stuff will happen.  When it's done, type "clear" and hit Enter, then "lsusb" and hit Enter.  Copy and paste the results and post them here as myth asks.

Oops, too late.  Looks like you figured this out, steffani.  Congratulations!

---

### Post by steffani on 2011-02-27
okay i hope im doing this right........

---

### Post by steffani on 2011-02-27
breathe steffani , just breathe.....
guys im lost......can i start over ......?

---

### Post by steffani on 2011-02-27
where i get stuck is that you say it will ask me for my password and it doesnt.....eeekkk

---

### Post by steffani on 2011-02-27
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
steff@innato:~$ 


see?

---

### Post by steffani on 2011-02-27
myth have you abandoned me? ](*,)

---

### Post by steffani on 2011-02-27
> **SeijiSensei said:**
> Start with this:  [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Follow the instructions to open a "terminal."  You'll see a window open on the screen with a "prompt" that looks something like this:

```
steffani@localhost:~$
```Type the command myth1914 gave you after the dollar-sign:

```
sudo apt-get update && sudo apt-get upgrade
```Hit the enter key.  You'll be asked to enter your password.  It's the one you always use to log in.  Stuff will happen.  When it's done, type "clear" and hit Enter, then "lsusb" and hit Enter.  Copy and paste the results and post them here as myth asks.

Oops, too late.  Looks like you figured this out, steffani.  Congratulations!
hey im still really stuck........can you help.......

---

### Post by myth1914 on 2011-02-27
Not abandoned...  Just got busy for a few.  Anyway.  Run the following next: ```
apt-get -f install
```

and post what it says next.  I had this issue with my Dell when I upgraded it.  Possibly a stuck package not completely installed.  Anyway, let me know.  (working til midnight, so I'll be on for a while yet, don't give up)

---

### Post by myth1914 on 2011-02-27
Also, it looks like all that's plugged in is a webcam.  Do you have the backup drive plugged in and powered on?

---

### Post by myth1914 on 2011-02-27
Well, it looks like a package install failed to finish downloading.  You will need to run the apt-get -f install to attempt pushing through it.  If not, you will need to remove the broken download manually and run synaptic to clean it up.  I've been through this lately, so i'll subscribe to this thread and wait to hear back from you...

---

