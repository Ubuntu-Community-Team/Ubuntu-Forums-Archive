---
title: "Kubuntu 6.06: kdesu working once, not running after that"
date: 2006-08-01
forum: Desktop Environments
---

### Post by hrvelic on 2006-08-01
Hello.
I have installed Kubuntu 6.06 recently, after first wiping out the upgraded ubuntu 6.06. I copied my old home folder over the new one after installation.
Since, then I have the following problem:
the first time I try to use an application that requires kdesu, it prompts me for a password and it works well. After that kdesu simply doesn't work. Asks me no prompt for password and doesn't run the application. :(
I also recall after the copy that KDE complained about DCOP configuration missing or something similar (it was something about DCOP that was not found), but after next login everything worked properly.
Anybody who could help me?

---

### Post by wieman01 on 2006-08-02
> **hrvelic said:**
> Hello.
I have installed Kubuntu 6.06 recently, after first wiping out the upgraded ubuntu 6.06. I copied my old home folder over the new one after installation.
Since, then I have the following problem:
the first time I try to use an application that requires kdesu, it prompts me for a password and it works well. After that kdesu simply doesn't work. Asks me no prompt for password and doesn't run the application. :(
I also recall after the copy that KDE complained about DCOP configuration missing or something similar (it was something about DCOP that was not found), but after next login everything worked properly.
Anybody who could help me?

To get more information, you could run the kdesu "<your application>" from a terminal. Post the output and we'll see what's wrong.

---

### Post by hrvelic on 2006-08-02
> **wieman01 said:**
> To get more information, you could run the kdesu "<your application>" from a terminal. Post the output and we'll see what's wrong.

I did that (long) before, with the same result. There is no message from kdesu. It doesn't exit with an error or another message, it just waits.
I have found a workaround for this problem today, but it really isn't much of a workaround: if I send a SIGTERM or kill any running (sleeping actually) kdesu processes _AND_ kdesud, the next time I run a kdesu-ed application, it behaves correctly.
This leads me to assume the problem is with kdesud, but I have no idea why or where to start looking.

---

### Post by Vlatko on 2006-08-02
> **hrvelic said:**
> I did that (long) before, with the same result. There is no message from kdesu. It doesn't exit with an error or another message, it just waits.
I have found a workaround for this problem today, but it really isn't much of a workaround: if I send a SIGTERM or kill any running (sleeping actually) kdesu processes _AND_ kdesud, the next time I run a kdesu-ed application, it behaves correctly.
This leads me to assume the problem is with kdesud, but I have no idea why or where to start looking.
i don't think there is much you can do. i had the same problems before, mainly with starting adept. seems there is a problem with kdesu. here's my thread, some explanations there.
[http://www.ubuntuforums.org/showthread.php?t=203467](http://www.ubuntuforums.org/showthread.php?t=203467)

---

### Post by hrvelic on 2006-08-02
> **Vlatko said:**
> i don't think there is much you can do. i had the same problems before, mainly with starting adept. seems there is a problem with kdesu. here's my thread, some explanations there.
[http://www.ubuntuforums.org/showthread.php?t=203467](http://www.ubuntuforums.org/showthread.php?t=203467)

Thank you for the information. The link didn't prove too much useful. The claim that kdesu conflicts in some way with sudo, which I tested, has proven false. At least for me. :/
However, the fact that it seems that this problem has existed since 5.04, leaves me quite perplexed. :(
Well, at least I know I can "reset" behavior to normal with a prompt termination of kdesud.

---

### Post by wieman01 on 2006-08-02
Does "gksu" have the same problem? Can you try?

Works well also under KDE.

---

### Post by Jucato on 2006-08-02
I've experienced this before in Breezy and a bit also in Dapper. What I do when kdesu doesn't seem to work is to open the Process Table (Ctrl+Esc), kill kdesu (no need to kill kdesud) and then try again. 

What I noticed in these instances was that the kdesu process is always paired up with a sudo process, and that killing kdesu also kills sudo, but not the other way around.

Anyway, I have not experienced that problem after upgrade to KDE 3.5.3. What KDE version are you using?

---

