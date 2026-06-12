---
title: "internet for ubuntu????"
date: 2006-07-08
forum: Desktop Environments
---

### Post by twitch19902008 on 2006-07-08
does anyone know where to get internet for ubuntu????:confused:

---

### Post by llamakc on 2006-07-08
America OnLine has a nice offering.










So what is your real question? Please restate it?

---

### Post by twitch19902008 on 2006-07-08
i was asking where can i get internet acces (dail-up) for ubuntu and no america online said they dont offer linux support

---

### Post by llamakc on 2006-07-08
Oh, you didn't use the word "access" so I figured you were having a network card/wireless card issue. My goof on AOL was a joke to poke you into posting more details.

Check with your local ISP's and the other bigwhigs like Earthlink for dialup. Most of them won't 'support' linux but you'll easily be able to connect to them all the same.

Good luck.

---

### Post by twitch19902008 on 2006-07-08
well like where at and sign on to aim so we can chat easlier dont mind myu scr name

---

### Post by llamakc on 2006-07-08
No thanks. Just buy internet service in your local area.

---

### Post by djheadley on 2006-07-08
As long as the ISP DOESN'T use their own software to dial and access the internet, you should be OK.  Examples of ISP who do use special software are Netzero, Juno, Earthlink, and AOL.

Take it from me, I use Netzero, you DON'T want to try any of these.

The AOL offer is for free e-mail only for those who have broadband connections. :(

---

### Post by twitch19902008 on 2006-07-08
i dont know how to set it up in ubuntu

---

### Post by llamakc on 2006-07-08
What are you trying to set up in Ubuntu? You really gotta start being more explicit if you want help.

---

### Post by twitch19902008 on 2006-07-08
like where do i put the dial up number

---

### Post by llamakc on 2006-07-08
[http://www.catb.org/esr/faqs/smart-questions.html](http://www.catb.org/esr/faqs/smart-questions.html)

Are you in Gnome? Are you asking what dialer program to use? What research have you done? Is your modem recognized yet?

---

### Post by twitch19902008 on 2006-07-08
ok yes i am gnome i dont know where to get my dialier no research and how do i know if my modem is reconized where do i find this crap on the web?](*,) ](*,) :confused: :confused:  :mad:  :mad: :evil: :evil:

---

### Post by twitch19902008 on 2006-07-08
srry i am really stupid at this thanks for what u have done and last ? no matter what where could i go to get good info on ubuntu?

---

### Post by llamakc on 2006-07-08
ubuntu.com is a great resource.

---

### Post by twitch19902008 on 2006-07-08
srry for any inconvinece y'all [http://www.dialup4less.com](http://www.dialup4less.com) says it supports linux i quess i will try it thanks again

---

### Post by orlox on 2006-07-08
If your modem is detected, the it should be pointed by /dev/modem, so you can configure dial-up to use it. I use wvdial to connect to the internet in ubuntu. To use it, you must first edit the file wvdial.conf (which should be located at /etc/wvdial.conf) as root. For example, my file is:

```

[Dialer Defaults]
Phone = 122311231
Username = myusername
Password = mypassword
New PPPD = yes

```

after setting this, you should be able to connect by running wvdial from a terminal. Simply open up a terminal, and write wvdial...

If your modem is detected, then this should work out...I think....

---

