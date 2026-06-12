---
title: "Java VM crashing unexectedly in both desktop and browser when playing Minecraft"
date: 2010-10-23
forum: Gaming &amp; Leisure
---

### Post by leemajors on 2010-10-23
Hi there,

I can only play Minecraft for about 5 minutes, using either the jar locally or playing through the browser before the game just dies. In browser the game goes to a white screen; locally the client just completely closes.

I've pasted the error log I get here: [http://pastebin.com/HpjYtaka](http://pastebin.com/HpjYtaka)

Any thoughts as to why this would be happening? Before it dies it plays perfectly fine. 

Running Maverick.

---

### Post by leemajors on 2010-10-31
Anyone able to help?

---

### Post by existent on 2010-11-14
> **leemajors said:**
> Hi there,

I can only play Minecraft for about 5 minutes, using either the jar locally or playing through the browser before the game just dies. In browser the game goes to a white screen; locally the client just completely closes.

I've pasted the error log I get here: [http://pastebin.com/HpjYtaka](http://pastebin.com/HpjYtaka)

Any thoughts as to why this would be happening? Before it dies it plays perfectly fine. 

Running Maverick.

I'm having a similar problem. I'm running it through wine, and after a few minutes it crashes to black. For what it's worth, I've found that decreasing the draw distance extends the time between crashes (which leads me to believe the problem is some sort of memory leak). Otherwise, the only thing I could think of would be to try running it in virtual box and see if that doesn't help.

---

### Post by leemajors on 2010-11-14
Hmm, thanks for your reply, I'll try the draw distance thing and see how much it improves.

As for running in virtualbox, well, my machines well enough spec'ed to play decent games, but sadly not well enough to be able to run an OS in a VM. It just chugs down and down.

---

### Post by Hamatt on 2010-12-26
I'm in the exact same boat as leemajors. Did that solution work for you?

---

### Post by leemajors on 2010-12-27
decreasing the draw distance did help a bit yep, but sadly didn't fix the problem. i gave up -- to be honest i think it's just that this machine is'nt well enough specced.

---

### Post by Kirboosy on 2010-12-29
I think it might be a spec issue for you too. Minecraft even though it looks terrible compared to other games still takes more resources than you might think.

[QUOTE=existent]I'm having a similar problem. I'm running it through wine, and after a few minutes it crashes to black. For what it's worth, I've found that decreasing the draw distance extends the time between crashes (which leads me to believe the problem is some sort of memory leak). Otherwise, the only thing I could think of would be to try running it in virtual box and see if that doesn't help.[/QUOTE]

Try running it natively

```
java -jar /home/existent/Downloads < or wherever you stored it>/Minecraft.jar
```You can make a launcher using this code to if you don't want to use terminal everytime to play. :)

---

