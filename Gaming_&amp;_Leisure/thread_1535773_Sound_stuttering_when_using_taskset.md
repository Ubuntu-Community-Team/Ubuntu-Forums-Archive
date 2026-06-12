---
title: "Sound stuttering when using taskset"
date: 2010-07-21
forum: Gaming &amp; Leisure
---

### Post by Klaue on 2010-07-21
Ubuntu 9.10 32bit

Hi there
I hope someone knows an answer
I'll first write down the story until now, just for some context:

I tried installing Unreal Tournament GOTY on my Ubuntu today. it was quite a task to get it running, but, using mainly [this thread]("http://ubuntuforums.org/showthread.php?t=82987"), I managed to do it. But now, UT ran way too fast. I found out that's because of CPU throttling - UT configures itself on the CPU speed at the start of the game, which is lower than the CPU speed when it runs. A solution for that is to use the "CPU Frequency Scaling Monitor" applet in the gnome bar and setting the CPU to the highest value (2.66 GHz for me). But now, UT was sometimes at the right speed and then after some seconds of play, suddenly way too fast again and later it was the right speed again. I figured out that this is because I have a quad core which causes UT to switch cores while playing. Setting CPU speed on all cores diddn't help, but setting the CPU speed on the first core and then using "taskset -c 0" did. But now, the sound stutters.

All in all, as soon as I restrain my game to a single core, the sound starts jerking. This happens using pasuspender as well as when just running it with nothing making pulseaudio busy, so pulseaudio seems to be, for once, not the problem.
Starting the game using the ALSA OSS wrapper kinda worked - the sound doesn't stutter anymore, but it's delayed for about 2 sekonds, which is really confusing,

Now, searching around a bit, I found out that taskset caused sound stuttering for [other people]("http://ubuntuforums.org/showthread.php?t=706812") as well (not just using UT), so this seems to be a more or less common problem. Still, I couldn't find any solution for it.

Anyone know of a possible solution for this?

As a side note, does anyone know how to change the CPU freq. in a script so I wouldn't have to manually set it every time I start UT (and set it back to "ondemand" when I stop playing)?

EDIT: Wow, that was quick. In just one hour, this thread got the top google result for *"taskset" sound issues*

EDIT:
Isn't it funny that I never get an answer here for stuff that can't be solved in mere minutes with google? But everytime someone tries to promote linux or even ubuntu, they're bound to mention the helpful people in the forums. Yeah right.
As someone on stumbleupon said, "I discovered that you'd never get an answer to a problem from Linux Gurus by asking. You have to troll in order for someone to help you with a Linux problem. For example, I didn't know how to find files by contents and the man pages were way too confusing. What did I do? I knew from experience that if I just asked, I'd be told to read the man pages even though it was too hard for me. Instead, I did what works. Trolling. By stating that Linux sucked because it was so hard to find a file compared to Windows, I got every self-described Linux Guru around the world coming to my aid. They gave me examples after examples of different ways to do it. All this in order to prove to everyone that Linux was better. Brings a tear to my eye... :') so true.. So if you're starting out Linux, I advise you to use the same method as I did to get help. Start the sentence with 'Linux is gay because it can't do XXX like Windows'". maybe I should try that the next time.[/letting off steam]

---

### Post by Klaue on 2010-07-21
I'm not usually one to push threads after mere hours, but I wanted to play with a friend this evening. Has nobody got an idea?

---

### Post by Klaue on 2010-07-21
OK, I found a not-perfect solution. When I change the audioDevice in the UT .ini and then start it using padsp, sound works, more or less
~/.loki/ut/System/UnrealTournament.ini
AudioDevice=ALAudio.ALAudioSubsystem -> AudioDevice=Audio.GenericAudioSubsystem

It still sounds like someone's rustling around with old newspapers, but at least it's playable.

---

