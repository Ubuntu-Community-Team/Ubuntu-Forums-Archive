---
title: "Please my desktop comp too slow in Ubuntu?"
date: 2008-07-10
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-10
My desktop has become very slow in ubuntu. It is P4 with 512 memory.
When I open xp it is alright. Firefox is very slow. I cannot scroll. It scrolls very slowly. Most of the time cpu is busy.

I need help please. I don't want to leave linux but I am having a lot of problems.

---

### Post by tamoneya on 2008-07-10
have you tried xubuntu.  It uses xfce instead of gnome and is much nicer on system resources.

[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by mirchichamu on 2008-07-10
Thanks Tamoneya for support. I will try but how to install it? Can it be installed on ubuntu? will you explain a little bit?

---

### Post by tamoneya on 2008-07-10
xubuntu is identical to ubuntu except that it is less processor intesive.  It gets installed the same way as ubuntu does.  You can test it out with the liveCD if you like.  It can either be installed over ubuntu or alongside it in a dual boot.

---

### Post by mirchichamu on 2008-07-10
Thanks a lot I will give a trial. And will inform you InshaAllah

---

### Post by snowpine on 2008-07-10
Hi Mirchichamu, Xubuntu is awesome, and Tamoneya makes an excellent suggestion.

However, Ubuntu should run just fine on a P4 with 512mb ram. So, I bet you we can fix your problem if we work together. :)

#1 thing I would suggest, are you using compiz desktop effects? If so, turn it off! You can do this from the Appearances dialog box (same place you change your wallpaper).

Also, if you run the System Monitor and go to Processes, you can see which application is eating up your CPU. Check it out and tell us what you find.

You might want to try Xubuntu anyway, but I think it's better to try it because you are curious, not because you are frustrated with something else, don't you agree? Anyway, all you need to do is open a terminal and type 'sudo aptitude install xubuntu-desktop'. Then, restart your computer. At the login window, click on Sessions and then choose Xfce (you'll notice there's also a Gnome option, that's what you can use to get back to Ubuntu). You can choose either Gnome or Xfce each time you log in, depending on how you are feeling that day. And if you ever get tired of Xubuntu, you can 'sudo aptitude remove xubuntu-desktop' to clean it up. Or, 'sudo aptitude remove ubuntu-desktop' if you decide to go with Xubuntu only.

Good luck!

---

### Post by sayakb on 2008-07-10
> **mirchichamu said:**
> Thanks Tamoneya for support. I will try but how to install it? Can it be installed on ubuntu? will you explain a little bit?

You don't need to get the liveCD to install XFCE. Just do:
```
sudo apt-get install xubuntu-desktop
```
at a terminal.
Also, at login prompt, press F10, click "Select session" and select XFCE.

Though I agree with snowpine. We can give a try to solve your Gnome problem first since your config is good enough to run gnome desktop easily. Post the output of the command:
```
top
```

---

### Post by mirchichamu on 2008-07-10
> **snowpine said:**
> Hi Mirchichamu, Xubuntu is awesome, and Tamoneya makes an excellent suggestion.

However, Ubuntu should run just fine on a P4 with 512mb ram. So, I bet you we can fix your problem if we work together. :)

#1 thing I would suggest, are you using compiz desktop effects? If so, turn it off! You can do this from the Appearances dialog box (same place you change your wallpaper).

Also, if you run the System Monitor and go to Processes, you can see which application is eating up your CPU. Check it out and tell us what you find.

You might want to try Xubuntu anyway, but I think it's better to try it because you are curious, not because you are frustrated with something else, don't you agree? Anyway, all you need to do is open a terminal and type 'sudo aptitude install xubuntu-desktop'. Then, restart your computer. At the login window, click on Sessions and then choose Xfce (you'll notice there's also a Gnome option, that's what you can use to get back to Ubuntu). You can choose either Gnome or Xfce each time you log in, depending on how you are feeling that day. And if you ever get tired of Xubuntu, you can 'sudo aptitude remove xubuntu-desktop' to clean it up. Or, 'sudo aptitude remove ubuntu-desktop' if you decide to go with Xubuntu only.

Good luck!

Thanks Snowpine for ur support.
I will give a trial and will let you know.

---

### Post by mirchichamu on 2008-07-10
> **LinuxIsInnovation said:**
> You don't need to get the liveCD to install XFCE. Just do:
```
sudo apt-get install xubuntu-desktop
```
at a terminal.
Also, at login prompt, press F10, click "Select session" and select XFCE.

Though I agree with snowpine. We can give a try to solve your Gnome problem first since your config is good enough to run gnome desktop easily. Post the output of the command:
```
top
```

Thanks a lot. I did the same as advised. I downloaded but after restart I couldn't find XFCE.at logon screen. There is last session, Gnome, xf script, failsafe something.......I ticked that xf? script but it is the same ubuntu.

What to do next?

---

### Post by sayakb on 2008-07-10
Are you sure you installed XFCE? Can you type the above command and copy and post its output here?

---

### Post by mirchichamu on 2008-07-11
> **LinuxIsInnovation said:**
> Are you sure you installed XFCE? Can you type the above command and copy and post its output here?

Thanks all of you. It looks that it is far better than before after installing Xubantu.
Once again millions of thanks.

---

### Post by mirchichamu on 2008-07-11
> **mirchichamu said:**
> Thanks all of you. It looks that it is far better than before after installing Xubantu.
Once again millions of thanks.

But I am unable to install in my laptop. Kindly refer to my other post on this topic.......... I cannot update my laptop. I shall be thankful if you help further how to solve the problem of updating my laptop.

---

### Post by project4 on 2008-07-11
> **mirchichamu said:**
> Thanks all of you. It looks that it is far better than before after installing Xubantu.
Once again millions of thanks.

my laptop was nice and fast with feisty fawn. After upgrading to heron i started using the compiz. I just switched it off, and my laptop is as fast as before.

i've been following this discussion and have one burning question: if xubuntu is better than ubuntu, why should we used ubuntu??

what is the differences? thanks!

---

### Post by unoodles on 2008-07-11
try this: sudo apt-get install preload
its a program that pre-loads libraries into RAM to speed up app startup times.

---

### Post by snowpine on 2008-07-11
> **project4 said:**
> i've been following this discussion and have one burning question: if xubuntu is better than ubuntu, why should we used ubuntu??

what is the differences? thanks!

That is a pretty loaded question, LOL. Neither is "better," they are just different. Think of Ubuntu as a bigger car that uses more gas, but is more comfortable to ride in. :)

---

