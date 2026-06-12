---
title: "LightDM not starting anymore"
date: 2017-01-10
forum: Desktop Environments
---

### Post by liam.gutierrez on 2017-01-10
My problem began when my LightDM background got blank all of a sudden, just white and plain. I could still log in as the login window appeared as always. However, in my quest to have a colorful background instead of a white, plain background, I tried to fix that. Unfortunately things got worse. I originally asked for help in this [forum]("https://ubuntu-mate.community/t/lightdm-blank-white-background-instead-of-my-chosen-picture/10964")

I got advised to reinstall lightdm:

```
sudo apt-get remove lightdm

  sudo apt-get purge lightdm

  sudo apt-get autoremove

  sudo apt get update
  sudo apt-get install lightdm
```

However, after doing that it somehow wrecked my lightDM completely because when I restarted no display manager started and I was looking at a dark monitor ](*,) Fortunately, I could still log into graphical mode with **startx** command but lightDM does not start up. 

To better help me, I included the log files found in /var/log/lightdm and copied/pasted them in pastebin.com:


[B][URL="https://pastebin.com/ag3NKp0P"]lightdm.log
http://pastebin.com/ag3NKp0P[/URL]

[seat0-greeter.log]("https://pastebin.com/pbNv1qpv")
[http://pastebin.com/pbNv1qpv](http://pastebin.com/pbNv1qpv)

[/B][B][x-0.log]("http://pastebin.com/P01nrWs2") 
[http://pastebin.com/P01nrWs2](http://pastebin.com/P01nrWs2)


[/B]Meanwhile, I am using the Slim display manager which is not the best (no remote login). Any help to fix my lightDM problem is very welcome!

---

### Post by liam.gutierrez on 2017-01-31
[B]UPDATE:

[/B]Replaced lightDM with another display manager, the old but still working SLIM. It works and I have a graphical login. SLIM doesn't boast many features but it loads quickly and solved my problem. I guess you can choose any display manager but SLIM is desktop agnostic. I close this thread as "solved" even though I would have preferred to have my lightDM working again yet such is life...

---

