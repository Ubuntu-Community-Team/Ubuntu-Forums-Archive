---
title: "Documentation for audio problems needs rewrite"
date: 2018-07-27
forum: Documentation and Community Wiki Discussions
---

### Post by John Nagle on 2018-07-27
"No sound" is a common Ubuntu problem. The documentation for dealing with this is outdated and misleading. See

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

which offers a 16-step procedure which looks like a cut and paste of everything various people tried in the last 10 years. Doing all that is almost certain to mess up your system.

There is a better way.

**Step 1: Test hardware and low-level drivers.**

Start by running "speaker-test".  See "http://manpages.ubuntu.com/manpages/xenial/man1/speaker-test.1.html". This tests the hardware and the low-level drivers. If "speaker-test" can't get some sound out of the speakers, nothing else is going to work. So the first step is to use speaker-test to find some hardware output that can make sound.

*This needs a simpler explanation than the man page. Actually, "speaker-test"'s default behavior should be to cycle through all the possible audio devices and put out a tone and the canned messages "Front Left", etc. on everything, in turn. Then you could just tell users "Run speaker-test in a command window and see which devices make sound." Right now, you have to get a list of device names and type them back in on the command line, which is lame.*

[B]Step 2: See if programs can get audio into the audio system

[/B][img]https://image.ibb.co/jh1YJo/pavuplaying.png[/img][B]
Pavucontrol

[/B]Start something playing audio. Run "pavucontrol" and see if the audio level bar moves. If it doesn't, audio is not making it from the source program to the audio system. 

[I]Not sure what to do if that doesn't work. This needs advice from a Ubuntu audio expert. But if audio isn't getting that far, it's not going to work.
[/I]
[B]Step 3: Deal with ALSA, etc.

[/B]Once steps 1 and 2 are working, you know that the low-level drivers hardware, and speakers are working, and that audio makes it from the source to the audio system. So something is messed up in the middleware that does switching, mixing, etc. A first step is to see that "pavucontrol" under "configuration" is sending output to some device found to work in Step 1. 
[I]
Beyond that, I don't know. This needs advice from a Ubuntu audio expert.



[/I]The documentation needs a rational troubleshooting procedure like this. Here's a start. Can someone else finish it? Thanks.

---

