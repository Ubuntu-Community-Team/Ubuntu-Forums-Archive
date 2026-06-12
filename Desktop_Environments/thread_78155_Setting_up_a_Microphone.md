---
title: "Setting up a Microphone?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by unexpected on 2005-10-17
Does anyone know if there is a microphone setup utility? I have a mic connected to the mic jack, but it when i try to record sounds it acts like it's not receiving any input.

Has anyone had any luck recording sound? I'm currently using Audacity as my audio in program...

---

### Post by David Marrs on 2005-10-18
Have you made sure the input volume is turned up? If you haven't, right click the volume applet and select "Open Volume Control" from the menu.

---

### Post by unexpected on 2005-10-18
After fooling around with it some, I did discover the volume panel. I enabled the microphone input at poof!

I can hear myself output through the speakers, so i know the microphone works!

However, when i go to Audacity and try to record sound, it acts like there's no input signal. I tried messing around with some of the input settings, but Audacity autopicks the mic device as /dev/dsp....from what i've read, this is right!

Has anyone else had a similiar problem?

---

### Post by Czajnick on 2005-10-26
I have exactly the same problem and also don't know what to do. Can anyone help?
--EDIT--
I managed to solve this problem. Just checked the "Full duplex" checkbox in kcontrol -> Sound and multimedia -> Sound system -> Hardware tab (this is my translation from Polish so it might be a little bit different on your system). I am using a Polish version of Kubuntu Breezy Badger.

If you want to check if a microphone is working properly, just run KRec, say something to the microphone and look at the bars on the left (you don't have to click the "record" button). They should be moving up and down.

---

### Post by lfrossati on 2005-10-26
Hi... 

I solved this problem in breezy changing the settings in MULTIMEDIA:

ALSA for OUTPUT
OSS for INPUT

then in the terminal type "alsamixer" and adjust the level for MIC and MIC BOOST. If you find "MM" under the words "MIC" and "MIC BOOST" type M to unmute the selected part.

Now its working perfectly here.

Regards,

Leonardo Frossati

Windows free since 2002.:D

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

### Post by zidkenu on 2008-06-22
google "ubuntu USB Microphone Logitech/Plantronics/Rocketfish"

---

