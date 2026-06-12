---
title: "Inspiron 9300 I8kmon Question."
date: 2009-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DevAdv on 2009-02-27
i have a dell inspiron 9300 that sits on my desktop pretty much 24/7.

it has two fans, cpu and gpu.

what im trying to do is setup i8kmon so that both fans run in the low state as soon as it boots.

when the cpu hits 50 degrees, kick them both into the high state.

and when they hit 45 degrees they go back into the low fan state.

would this be the correct setup for that?

> 
set config(0) {{-1 0} -1 10 -1 10}
set config(1) {{-1 1} 15 50 15 50}
set config(2) {{-2 2} 45 80 45 85}
set config(3) {{-2 2} 70 128 75 128}
ty in advance for any help given 

ty in advance for any help given :)

---

### Post by motin on 2009-02-28
When you use that config, does it work as expected? You have the i8kmon applet? And the sensors applet? That should be all to see if it works.

---

### Post by DevAdv on 2009-02-28
i havent installed lmsensors or the applet from your other post.

i wanted to get this setup without having any kind of gui visualization. 

ill try it tonight and see if it works.

---

### Post by DevAdv on 2009-03-01
-edit-

---

### Post by mihai.ile on 2009-03-02
did you followed this post?
[http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

After install you only need tio confugure that file and modprobe the i8k at startup (as explained in the post). Right now you can check fan info but you need to add the daemon at gnome's startup so that it will change the fan speed according to the values in the config file. no gui is needed.

---

### Post by DevAdv on 2009-03-02
i got i8k to work. thats not the problem.

i need help configuring the fans. but im testing now so i will report back if those settings i posted above work.

---

