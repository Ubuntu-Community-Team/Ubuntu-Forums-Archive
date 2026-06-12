---
title: "tuxguitar doesn't make any sound!!!"
date: 2009-04-14
forum: General Help
---

### Post by silverdrop on 2009-04-14
I dont know why tux guitar does not make any sound. the volumen is up to the max and still nothing. PLZ help me! thanx!!!:guitar:

---

### Post by askreet on 2009-04-14
I don't know what that is, but you should try running it from a terminal window, and watching for output that might explain why it cannot output to your sound device.

HTH,
askreet

---

### Post by rbc on 2009-04-14
I had the same problem, but perhaps not from the same cause. What fixed it for me was installing (from Synaptic):
tuxguitar-alsa and tuxguitar-jsa
If that does not work, do as askreet suggested and post back

---

### Post by silverdrop on 2009-04-14
thanx rbc! that was the problem. I didn't download thos package. thanx askreet, but im a little stupid to work with the terminal, i know that is more easy, but i dont know so well the commands. but thanx anyway! IT WORKS! :D

---

### Post by llamaSniper on 2009-04-25
I installed the packages specified, and I still have no sound.  There is no error, and when I run it in terminal, I have no output.  It opens and goes through all the tabs, but it does not make any noise.

---

### Post by Darkshade on 2009-04-26
> **llamaSniper said:**
> I installed the packages specified, and I still have no sound.  There is no error, and when I run it in terminal, I have no output.  It opens and goes through all the tabs, but it does not make any noise.

Last time I had the same problem, though I had the extra tuxguitar packages. What fixed it was going to Settings -> Sound and selecting Real Time Sequencer under MIDI Sequencer and Java Sound Synthesizer under MIDI Port.

---

### Post by llamaSniper on 2009-04-26
Yea, I just tried that, and that didn't help.  Is there some plugin that I need? (I already got the ones mentioned above)

---

### Post by linuxvacuum on 2009-04-26
Thanks for the java method! What's weird is that I hear a piano sound when it's supposed to be an overdriven guitar... Anyways before I had that solution, I used that one from another post :

Install the timidity MIDI sound server.
```
sudo apt-get install timidty
```

Run it then tuxguitar.
```
timidity -iA -Os &
tuxguitar
```

Then choose the appropriate MIDI driver in the menu of tuxguitar. Timidity 0 or something like that.

---

### Post by Kareeser on 2009-04-26
llama:

```

sudo apt-get install timidity
sudo /etc/init.d/timidity restart
```

---

### Post by llamaSniper on 2009-04-26
Thankyou SOOOOO much, the timidy MIDI change thing fixed it!!!! :D now I can get back to what I was doing!!!:guitar:

---

### Post by Failbot on 2009-04-28
This is what I did to get TuxGuitar working nicely with PulseAudio. This lets you run other audio apps at the same time, meaning you don't need to close TuxGuitar to listen to an MP3 for example.

Install timidity if you haven't already:```
sudo apt-get install timidity
```

Disable timidity startup daemon:```
sudo update-rc.d -f timidity remove
```
That stops timidity running as a daemon at startup. It runs as root user without PulseAudio support and so hogs the sound card when midi is playing. Doing this means users will need to run timidity manually before using apps that need the midi synth.

Modify the command to startup TuxGuitar to run timidity first, and shut it down when finished:
Go to System -> Preferences -> Main Menu, Sound & Video section, select TuxGuitar, click Properties. Change the startup line to:```
sh -c "timidity -iA -Os & tuxguitar %F && killall timidity"
```

Run TuxGuitar. In Tools -> Settings, Sound section choose "Real Time Sequencer" and "TiMidity port 0".

That's it! To test that everything is working how it should, you should be able to fire up an MP3 in Totem at the same time TuxGuitar is playing back midi.

Note: I'm a bit of a newb at all this, so I'm not sure if this is the best solution, but it works for me so I'm happy. :)
There is some discussion about running timidity at user logon and shutting it down at logout here: [https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/210472](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/210472)

---

### Post by Kleist on 2009-04-28
Thanks Failbot!
Your method worked for me!:guitar:

---

### Post by Kareeser on 2009-04-30
I find that a startup script "sudo /etc/init.d/timidity restart" works just as well.

To each his own :)

---

### Post by agitdd99 on 2009-05-08
> **Failbot said:**
> That's it! To test that everything is working how it should, you should be able to fire up an MP3 in Totem at the same time TuxGuitar is playing back midi.

Thanks a lot dude! you described it so precisely! :guitar:

---

### Post by MyR on 2009-05-28
I got sound to work by installing tuxguitar-jsa then changing the "MIDI Port" in tuxguitar settings to Gervill.

peace

---

### Post by brunolabs on 2009-11-01
> **Kareeser said:**
> llama:

```

sudo apt-get install timidity
sudo /etc/init.d/timidity restart
```

Had the same problem. The restart code solved it.
Thanks!!

---

### Post by 55tptag on 2009-11-19
> **MyR said:**
> I got sound to work by installing tuxguitar-jsa then changing the "MIDI Port" in tuxguitar settings to Gervill.

I had Gervill working with Tuxguitar in earlier versions of Ubuntu.  But, I don't think Gervill is available in Ubuntu 9.10 from their repositories.

---

### Post by phulo1 on 2010-01-02
I installed the two packages and worked fine, ubuntu 9.04 by the way:guitar:

---

### Post by miguel.guilherme on 2010-09-06
Well, now I've got no file on /etc/init.d/timidity even after reinstall the package

---

### Post by Myon87 on 2011-07-26
Problem for me is that those java midi sounds are awefully bad sounding.

---

