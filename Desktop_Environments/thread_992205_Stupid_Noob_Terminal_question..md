---
title: "Stupid Noob Terminal question."
date: 2008-11-24
forum: Desktop Environments
---

### Post by wildbillkelso on 2008-11-24
Hi all!.

Im new to linux and have had a lot of fun trying diferent distros but Ubuntu seems to be the best supported, and do all I want to. Thanks very much Canonical!

Anyway, I am trying to get get a game working in WINE and there is a guy posted some advice on the wine forum but it does not work in Ubuntu. He was using Slackware wich I believe is not for new users. He suggested in terminal to type "-s /dev/input/js0 /dev/js0" and when I do it says bash bad command. With my limited noob knowlege I figured this would need to be a root command or something, so i typed sudo and return and then /dev/input/js0 /dev/js0.

Still no luck.

I am using Intrepid and I need to configure several input devices like the joystick, throttle and rudder pedals.

If anyone can offer any advice I would be most gratefull. Sorry if it is a stupid question!

Thanks and best regards.

Tim

---

### Post by taurus on 2008-11-24
I think you are missing a crucial command before the -s.  Looks to me like you want to link /dev/js0 to /dev/input/js0!

```
sudo ln -s /dev/input/js0 /dev/js0
```

---

### Post by wildbillkelso on 2008-11-24
Hi Taurus.

Thank's for the superfast reply.

The full advice says "Open up terminal and type the following: ln -s /dev/input/js0 /dev/js0. Wine has a habit of looking for the joystick in /dev instead of /dev/input."

I will give the code you suggest a try.

Cheers.

Tim

---

### Post by taurus on 2008-11-24
> **wildbillkelso said:**
> Hi Taurus.

Thank's for the superfast reply.

The full advice says "Open up terminal and type the following: **[COLOR="Blue"]ln[/COLOR]** -s /dev/input/js0 /dev/js0. Wine has a habit of looking for the joystick in /dev instead of /dev/input."

I will give the code you suggest a try.

Cheers.

Tim

In Slackware, you log in as root so you can just run the command as it.  But in Ubuntu, you need to include sudo before the command if you want to run that command with root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wildbillkelso on 2008-11-24
Yep it works.

Thanks for the link. I am now free of the need for windows as Ubuntu does all I need.

Thank you for the speedy support and providing the information to further my understanding.

Linux is fascinating I wish I had discovered it sooner!

I have also got two of my freinds trying Ubuntu and they like it a lot to. Trying to do my bit for the community.

KILL BILL!

Many thanks Taurus and best regards.

Tim

---

