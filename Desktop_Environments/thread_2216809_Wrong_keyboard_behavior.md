---
title: "Wrong keyboard behavior"
date: 2014-04-14
forum: Desktop Environments
---

### Post by gabriele.barni on 2014-04-14
[COLOR=#333333][FONT=UbuntuRegular]I am encountering a very weird error recently, that I cannot figure out to solve...I have surfed for hours and hours without any solution.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I explain: I have an Asus S301L , with Ubuntu 12.04 and an Italian keyboard; every time I log in, some key on my keyboard does not work properly:[/FONT][/COLOR]

[LIST=1]
[*]p priduces *
[*]0 produces /
[*]- produces +
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]But also others...for example, It took time for me to write just this message...so frustrating sometimes.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The only way to have things again to work properly is to type in a shell:[/FONT][/COLOR]

```

setxkbmap it

```

[COLOR=#333333][FONT=UbuntuRegular]And it starts again to work, just for a (indefinite) duration of time , then, things, again, are wrong.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I hope to be clear and have explained my problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Anyone can help me ?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks in advance for all the answers you'll give me[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Cheers[/FONT][/COLOR]

---

### Post by sudodus on 2014-04-14
Welcome to the Ubuntu Forums :-)

I suspect that you use some software (some application program), that resets your keyboard to something else than Italian.

- Is is OK when you log in after shutdown or reboot? Or is it wrong from the very beginning?

- Have you activated or run some program, that uses a different language?

---

### Post by gabriele.barni on 2014-04-14
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

I suspect that you use some software (some application program), that resets your keyboard to something else than Italian.

- Is is OK when you log in after shutdown or reboot? Or is it wrong from the very beginning?

- Have you activated or run some program, that uses a different language?


Thanks for the answer.

the problem starts at the login,and after reboot, moreover, after I restored the layout, I don't really know why, it is broken again...

Is there a way to do a complete reset of xkb, or xmodmap ?


could it be a solution?

---

### Post by sudodus on 2014-04-14
Can you remember if you have installed some program at the time when the keyboard started to change like this? Or could it be a hardware error, some that is 'almost' broken? For example, what happens if you use another keyboard (I mean the physical device)?

It should be possible to check if it is a software error by booting and running 'a live session' for a reasonably long time from an Ubuntu desktop install DVD/USB drive. If the Italian keyboard stays when running live, we can be pretty sure, that it is a software problem.

When browsing the internet for ***ubuntu install keyboard locale*** I found several useful links, for example this one

[http://www.howtogeek.com/howto/17508/add-keyboard-input-language-to-ubuntu/](http://www.howtogeek.com/howto/17508/add-keyboard-input-language-to-ubuntu/)

---

