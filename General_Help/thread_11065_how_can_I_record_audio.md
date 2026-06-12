---
title: "how can I record audio?"
date: 2005-01-13
forum: General Help
---

### Post by xutopia on 2005-01-13
I've been asked to record my name in a wav file to send to someone.  I tried sound-recorder, arecord and even audacity.  I cannot seem to get any of these working.

sound-recorder : freezes when I press CTRL+C, doesn't write to file.
arecord: doesn't do anything at all.
audacity: get following error message: Error while opening sound devices.  Please check the output device settings and the project sample rate.

What should I check?  I know skype works so my microphone isn't the issue (I hope).  Anyone have any clue?

Thanks in advance.

---

### Post by wulf on 2005-01-14
How are you running *audacity*? I found it only worked if I ran it from the command line, which turned out to be a problem with *esd*. See:

[http://www.ubuntuforums.org/showthread.php?t=6551](http://www.ubuntuforums.org/showthread.php?t=6551)

for more details.

Wulf

---

### Post by alainhenry on 2005-01-14
I had to fiddle with Alsamixer to record sound using Mandrake.  I assume it's the same with Ubuntu, whch uses alsa too (I didn't try yet with Ubuntu).  See thread: 

[http://groups.google.be/groups?q=sound+recording+alain+henry&hl=fr&lr=&group=alt.os.linux.mandrake.*&selm=pan.2004.05.23.16.28.50.728600%40ibelgique.com&rnum=1](http://groups.google.be/groups?q=sound+recording+alain+henry&hl=fr&lr=&group=alt.os.linux.mandrake.*&selm=pan.2004.05.23.16.28.50.728600%40ibelgique.com&rnum=1)

To put it shortly, I ran alsamixergui (I think it is in the multimedia menu, but you might have to install it or run alsamixer from a terminal.  There are there a number of sliders that you will have to adjust, depending on the input device you use.  In my case, using the line input, I had to adjust the volume sliders 

'ADC' = Throughput `line in` port
'ADC Capture' = Record from `line in` port
(Left hand 'Digital' input also has to be unmuted to record)

If you're using a microphone, you might need to experiment with other sliders.  

Good luck.

Alain

---

