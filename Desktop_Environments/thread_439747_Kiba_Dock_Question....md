---
title: "Kiba Dock Question..."
date: 2007-05-11
forum: Desktop Environments
---

### Post by volksolwagen57 on 2007-05-11
I installed kiba-dock and made it a session on start up. now every time it starts up the bar is there and so are the icons but now the icons don't have a transparent backdrop, that is, the icon is there with a little black box behind it. I restart kiba-dock and it goes away. it happens every time i boot up. what can i do? i appreciate your help in advance.

---

### Post by FuturePilot on 2007-05-11
You need to be running Beryl or Compiz.

---

### Post by darkmaster on 2007-05-11
Kiba is not supported by Ubuntu. In any case, yes, you need a composite manager but it doesn't have to be Beryl or Compiz. If you don't whant any particular effect except for trasparencies and fading, you can also download from synaptic 
xcompmgr
But in any case, you need to start xcompmgr, beryl or compiz in the booting sequence, add one of them to the session as you did for Kiba but remember: never run more than a composite manager at a time.
After that: have you ever looked for Avant Window Navigator? If you need a stable and cool dock it may be better than Kiba. It has a different style and works differently, it has no phisics.... it is different. Give it a shot!

---

### Post by volksolwagen57 on 2007-05-11
where can i find the avant window manager? and i do have both beryl and compiz and kiba-dock in the start up program sessions. all of them start up. is this bad. what i really wanted was just a minimalist dock that allows the icons to swell like in osx. i don't like how the icon spins when you select a program.
Oh! and how do i uninstall kiba-dock if i wanted to can i keep it without ruining it with the avant install?

---

### Post by darkmaster on 2007-05-11
> **volksolwagen57 said:**
> where can i find the avant window manager? 

Avant Window Navigator. Look here: 

[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository)

And follow the simple instructions.

> **volksolwagen57 said:**
>  and i do have both beryl and compiz and kiba-dock in the start up program sessions. all of them start up. is this bad. 

Very bad. That's why you're having problems. Choose: Compiz or Beryl. Only one has to be autostarted at the same time! That's what happens in you PC: Compiz or Beryl starts, then the other one starts too, they go in conflict and terminate each other (Really they crash) so you don't have any composite manager running anymore and Kiba Dock becomes black (Since it has no trasparency anymore). Only start ONE of them. So in Feisty, before you can autorun Beryl, you have to deactivate Desktop Effects, for example.

> **volksolwagen57 said:**
>  what i really wanted was just a minimalist dock that allows the icons to swell like in osx. i don't like how the icon spins when you select a program. 

Then Avant is for you. It is splendid: doesn't have the zoon effect like the one in OSX but has another jumping effect you'll love. And it is quickly evolving. It works very well like OSX dock, because you can drag and drop into it your program icons and it'll work like a launcher but if you open a program in the launcher, it won't mess up with the taskbar like Kiba does! Plus, moving your mouse over an opened application, will trigger the wonderfull Beryl effect that shows you a miniature of opened windows! :) Avant is really wonderfull.

And beside that, in Kiba to can disable the rotating effect if you don't like it. Look at the kiba settings, it is simple to set. This is the most customizable dock around for sure, even if it is a bit messy (In coding too) and CPU resources hungry... Avant, on the other side, is really light. 

> **volksolwagen57 said:**
>  Oh! and how do i uninstall kiba-dock if i wanted to can i keep it without ruining it with the avant install?

Of course they can live togeter but I recommend you to start only one of them at a time. And if you wish you can uninstall Kiba simply using synaptic. It is not different than uninstalling any other application if you used a repository.

---

