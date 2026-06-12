---
title: "XGL/Compiz problem"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Flaringo on 2006-09-24
Hello.

Well, maybe the number one reason I installed Linux this time, was because I saw XGL. It just looked so awesome, that I had to throw in Linux on my disc nr.2 again. :P It was a real let-down when I heard they had taken down the compiz-files. After searching for it since yesterday, I found this [http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29) guide. I followed it from start to end, but when I started it, I got this error: ```
flaringo@Flaringo:~$ thefuture
gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension
```

What do I do now? I know people that has got it working! 

I really need some help with this now. [-o< 

-- Flaringo

---

### Post by ayoli on 2006-09-24
1) have you enable composite extension in your /etc/X11/xorg.conf like this:
```
Section "Extensions"
        Option  "Composite"     "enable"
EndSection
```
2) else maybe you miss libxcomposite, then:
```
sudo aptitude install libxcomposite1
```
then restart X and retry

---

### Post by Flaringo on 2006-09-24
Guess that helped a little. Thanks. But now I'm stuck with this error: ```
gnome-window-decorator: Another window decorator is already running
flaringo@Flaringo:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

And right now I can't really move any window or anything like that. xD

---

### Post by ayoli on 2006-09-24
try from command line:
```
killall gnome-window-decorator
```
then run your start script again

---

### Post by spockrock on 2006-09-24
you may get an answer from [www.compiz.net](www.compiz.net) to your problems.

---

### Post by Flaringo on 2006-09-24
> **ayoli said:**
> try from command line:
```
killall gnome-window-decorator
```
then run your start script again

That didn't work. :-\

---

### Post by Flaringo on 2006-09-24
Isn't there anyone that can help? :(

---

### Post by Flaringo on 2006-09-24
Sorry, I need to bump this again. I really, really need some help with this.

---

### Post by distroman on 2006-09-24
I think the best thing you can do right now is to wait.
Have a look around the forum. 
[http://forum.beryl-project.org/](http://forum.beryl-project.org/)
As I understand it, beryl will be available shortly.

---

### Post by spockrock on 2006-09-24
what is the output after you killall gnome-window-decerator and then run your start up script.

again compiz.net, now forum.beryl-project.org will give a much quicker, solution. lol distroman beat me to it.

---

### Post by ayoli on 2006-09-25
they're right, beryl will be a great GL Desktop experience, and comes out in few days i think.
btw, to help you more with your compiz problem: what version of compiz do you use (quinn, vanilla, which version number)

---

