---
title: "Compiz Fuzion"
date: 2008-01-27
forum: Desktop Environments
---

### Post by 34.50 on 2008-01-27
I just installed triple boot Windows XP Pro/ eComStation OS/2 RC4 / Ubuntu 7.10 Gutsy Gibbon w/ Grub 1.5. Previously, I had a dual boot XP Pro/Ubuntu a while back, and had Compiz working. I do remember it was hard to get it running. 

I have an ATI x200M (iintegrated 32MB, upto 128MB) and I have the ATI restricted driver installed. I want to get Compiz-Fuzion working again. When I goto enable the desktop effects, it says, "The Composite extension is not available." I vaguely remember that you had to edit a file called the x11org.conf (or something similar) file to enable composite thing. 

So, can I get some help please? 

Thanks in advance.

---

### Post by santiagoward2000 on 2008-01-27
> **34.50 said:**
> I just installed triple boot Windows XP Pro/ eComStation OS/2 RC4 / Ubuntu 7.10 Gutsy Gibbon w/ Grub 1.5. Previously, I had a dual boot XP Pro/Ubuntu a while back, and had Compiz working. I do remember it was hard to get it running. 

I have an ATI x200M (iintegrated 32MB, upto 128MB) and I have the ATI restricted driver installed. I want to get Compiz-Fuzion working again. When I goto enable the desktop effects, it says, "The Composite extension is not available." I vaguely remember that you had to edit a file called the x11org.conf (or something similar) file to enable composite thing. 

So, can I get some help please? 

Thanks in advance.

Hi there!
First you have to install the restricted drivers. Go to **System/Restricted Drivers Manager** and check your card.
Then, you'll need to install XGL. Open **Synaptic** and look for **xserver-xgl**, or open a terminal and type:
```
sudo apt-get install xserver-xgl
```
Then, restart your computer and try to enable Compiz.
Good luck! :KS

---

### Post by 34.50 on 2008-01-27
> **santiagoward2000 said:**
> Hi there!
First you have to install the restricted drivers. Go to **System/Restricted Drivers Manager** and check your card.
Then, you'll need to install XGL. Open **Synaptic** and look for **xserver-xgl**, or open a terminal and type:
```
sudo apt-get install xserver-xgl
```
Then, restart your computer and try to enable Compiz.
Good luck! :KSGreat! That worked, but where are the advanced compiz options?

---

### Post by santiagoward2000 on 2008-01-27
> **34.50 said:**
> Great! That worked, but where are the advanced compiz options?

Glad to help!
You need to install **compizconfig-settings-manager** for those options.
Cheers!

---

### Post by 34.50 on 2008-01-27
Thanks Mate!

---

### Post by santiagoward2000 on 2008-01-27
> **34.50 said:**
> Thanks Mate!

No problem! As I said before, I'm glad to help! :popcorn:

---

### Post by 34.50 on 2008-01-27
Lol, while you are here, can you help me out with another thing? I have a Logitech Mx400 mouse, and it has buttons that on Windows in a browser you can use for back and forward. Can you tell me how to register those buttons for those events?

Thanks again :)

---

### Post by santiagoward2000 on 2008-01-27
> **34.50 said:**
> Lol, while you are here, can you help me out with another thing? I have a Logitech Mx400 mouse, and it has buttons that on Windows in a browser you can use for back and forward. Can you tell me how to register those buttons for those events?

Thanks again :)

Well, honestly, I have no idea :confused:
I just found this thread about it, but I don't know if it works (my mouse doesn't have all those buttons)
[http://ubuntuforums.org/showthread.php?t=364775]("http://ubuntuforums.org/showthread.php?t=364775")
I hope this helps, and sorry I can't help you any more...
Good luck!

---

### Post by 34.50 on 2008-01-27
Thanks! I'll mess around with it. 

I guess this thread can be closed, I won't be checking back

---

### Post by santiagoward2000 on 2008-01-27
> **34.50 said:**
> Thanks! I'll mess around with it. 

I guess this thread can be closed, I won't be checking back

Cool! Just one more thing: Can you mark it as solved? Go to the **Thread tools** option at the top and select **Mark this thread as solved**.
Cheers!

---

