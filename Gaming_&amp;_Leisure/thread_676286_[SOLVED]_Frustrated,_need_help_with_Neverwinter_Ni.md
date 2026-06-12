---
title: "[SOLVED] Frustrated, need help with Neverwinter Nights fix.."
date: 2008-01-23
forum: Gaming &amp; Leisure
---

### Post by trooperchix on 2008-01-23
I've tried absolute beginners, I've tried elsewhere, but can't seem to get the full skinny on how to implement the dual core processor video problems with NWN..  I get part of the instructions, but only part.  Would someone kindly  walk me through this from beginning to end without making any assumption about my knowledge of Ubuntu?  I'm a brand new convert, and am sold so far, but I don't know the scripting language or whatever to do things right.  Assume I am a regular born backwards dolt.  Write this for a total noob to understand.  I just want to cry.

The fix info is here:

[http://nwn.bioware.com/forums/viewtopic.html?topic=484346&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=484346&forum=72)

I'm dying here, please help.  I've tried as hard as I can, and I'm just plain stumped.

Thanks ahead of time.

PS I run Feisty, no compiz no beryl.  Don't know if that is pertinent information, but there it is...

---

### Post by kizmet_x on 2008-01-23
To be honest, I just installed the windows version with wine. I had heard there were  a lot of problems with the native linux version, but in wine it runs almost flawlessly.

---

### Post by DoktorSeven on 2008-01-23
In the thread you linked to, note the reply by "zzqzzq_zzq"; this is the best place to start. 

You will have to open a command prompt, if you don't know where that is, just hit Alt+F2 and type **gnome-terminal** (assuming you're using plain Ubuntu; Kubuntu should type **konsole** but I have no idea what Xubuntu uses by default).

Once there, you need tools to compile programs with.  Type:

**sudo apt-get install build-essential**

It will ask for your password.  Type it in (there'll be no stars or any indication that it's being typed, but it's working).  If it asks you if you're sure you want to install the things it lists, type y then enter.

Now we'll need to follow along with what "zzqzzq_zzq" posted.  Type these, one line at a time:

```

mkdir /tmp/run
cd /tmp/run
wget http://ccur.com/oss/run-3.0.tar.gz
tar zxfv run-3.0.tar.gz 
cd run-3.0
./configure --disable-shared
make

```

(Note; I modified the line starting with "gzip" to simplify it a bit.)

If there are any ERROR messages printed at the end of any step, copy and paste them all here and we'll see what you might need.  You can safely ignore any "Warning" messages, especially during the "make" step.

Now copy "run" to your /usr/local/bin directory so your system will recognize it when you use it:
```
sudo cp /tmp/run/run-3.0/run /usr/local/bin
```
If it asks for your password again, give it (though it may remember it if you typed it before).

Since I don't have NWN installed at the moment, I'm not sure which file they want you to edit to modify like that, though I suppose it's whatever program you run to launch Neverwinter Nights.  Just open it with a text editor like gedit or kwrite and find the line they want you to modify.

Post back if you need further help.

---

### Post by trooperchix on 2008-01-25
aaargh, how do I delete this sucker.  Then I have a few questions about the nwn gold installer that's out there.  they're quick "duh" questions, but I'm not quite confident in my skills.  

If NWN Linux binaries are causing the problem, then off with them then!!   LOL!!  (uh, so how do I do that?)

---

