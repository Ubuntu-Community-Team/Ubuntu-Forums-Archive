---
title: "[SOLVED] Compiz-fusion stops working after update"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by mahasmb on 2007-06-28
Alright...

So I had Beryl working fine. Then Ubuntu notifies me that Beryl has some updates. I go through with them and Beryl stops working. So I decided it was a good time as any to get Compiz-fusion. I install and Compiz-fusion works (more or less). Then Ubuntu notifies me of Compiz-fusion updates. I update Compiz-fusion and it stops working. So I look through the forums to see if anyone else has had my problem. I find this thread 

>> [http://ubuntuforums.org/showthread.php?t=447317&highlight=compiz-fusion+update](http://ubuntuforums.org/showthread.php?t=447317&highlight=compiz-fusion+update)

> **DarkN00b said:**
> After I updated my Beryl this morning, it crashed and did not default to Metacity. Fortunately I had read that there was a problem with yesterday's update and had set Ubuntu to start in Metacity. So I open a terminal window and type "Beryl". Instantly I have borderless windows and an error about the benchmark plugin.

"AHA," I say to myself. 

So I type "Metacity" to restart my window manager. Then I start beryl-manager and go to Extras and disable the benchmark plugin. I restart Beryl and all is well in Ubuntuland. Beryl is running just fine now.

Oh yeah, I'm using Trevino's SVN as well.

and I follow DarkNoob's advice. Now my updated Beryl is working. (It starts with the Beryl SVN splash screen instead of the old Beryl 0.2.0 rc3 Splash screen)

So I have my Beryl working, but not my Compiz-fusion. Is there any way I can get Compiz-fusion working again? (I wasn't so sure that I could have both Beryl and Compiz-fusion working, but I think I remember someone else in the forums saying it was possible)

---

### Post by jackmc on 2007-06-28
you can have both (i do), but I'm not sure how to fix your problem sorry.

---

### Post by hyperair on 2007-06-28
Well, try posting the output of ```
compiz --replace
``` and we'll see if we can help.

---

### Post by Nossie on 2007-06-28
> **hyperair said:**
> Well, try posting the output of ```
compiz --replace
``` and we'll see if we can help.

I'm also having a similar problem since the update....

Compiz effects appear to work but I'm still stuck with the metacity themes and not the emerald ones?

sorry nevermind... fixed with 

> emerald --replace

---

### Post by Nossie on 2007-06-28
ack ok...

I cant seem to get alt+F2 to work to run 

emerald --replace

and although I have  Compiz setup in sessions to run 

```
compiz --replace
``` 

on startup... the same does not seem to work for emerald? which I also have in sessions

```
emerald --replace &
```

can anyone give me a clue how to get both working? I can enable emerald from terminal but it quits when I close the terminal.

> ian@Jupiter-ubuntu:~$ emerald --replace &
[1] 7182
ian@Jupiter-ubuntu:~$ 
(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)


ty
Ian.

---

### Post by Nossie on 2007-06-28
*Sigh* sorry for being stupid...

ok emerald works fine now...
Compiz works fine now
and run (alt+f2) works fine now....

what happened was...
I noticed there were some compiz-fusion etc updates today...
I updated and it froze at a certain point... I closed the update manager and checked for updates again... no updates were shown... so I thought things were fine.

I restarted X and that was when all my problems began and I posted in this thread...

I thought I'd have another check for updates just in case and found another lot of compiz updates and once they installed fine.... all my problems went away...

sorry for cluttering up the forum heh 
:)

Ian.

---

### Post by hyperair on 2007-06-28
Just a piece of advice: If you run any application in the terminal with the "&" after it, and you want it to continue even after closing the terminal, type "exit" instead of pressing the "X" button. Alternatively, you can keep running the command "disown" until "jobs" has no output.

---

### Post by Nossie on 2007-06-28
ty,

 I always believed that & ran tasks in the background and allowed you to run other commands in the terminal...

but experience with ubuntu ... it would APPEAR (I'm probably doing something wrong) that & is being ignored unless I run the command from alt-f2 in gnome. (without the &)

The problem I was having with compiz and emerald.. the terminal was not returning back to the bash prompt even using & so I couldn't type exit even if I wanted to...

dont really understand that and flys in the face of the experience I've had with other distros.

you'll notice from my past posts

```
(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)
```

does not return to the bash prompt

ty though for your advice.

---

### Post by hyperair on 2007-06-28
Actually it does bring you back to the prompt:

```

an@Jupiter-ubuntu:~$ emerald --replace &
[1] 7182
**ian@Jupiter-ubuntu:~$ **
(emerald:7182): Wnck-WARNING **: Unhandled action type (nil)

```

The bolded part is where the prompt was. It's just that the output channeled through the standard error still comes through to the terminal, so it looks as if there's no prompt there. If you don't believe, me try pressing enter, after running some application with the &. For example, try "compiz --replace &" in the terminal, and after it's finished outputting, press enter. The prompt will appear again. Even if you don't press enter, you can just type exit and press enter and the window will go away. Believe me, I'm using Ubuntu too.

---

### Post by Nossie on 2007-06-28
aha !! fantastic :D

I never realised the prompt was still there... I just thought it was caught up in the error log...

ty again!!

---

### Post by mahasmb on 2007-06-29
I got my Compiz-fusion working again through this thread:

[http://ubuntuforums.org/showthread.php?t=486540&highlight=compiz-fusion](http://ubuntuforums.org/showthread.php?t=486540&highlight=compiz-fusion)

---

### Post by Mr Greencastle on 2007-06-29
I'm glad you found that fix, it helped me too.
I believe the Fusion team issued another update, so anyone else shouldn't run into this problem.

Mr Green

---

