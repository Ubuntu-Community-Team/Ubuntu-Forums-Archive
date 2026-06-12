---
title: "Thunderbird problem"
date: 2006-09-05
forum: Desktop Environments
---

### Post by sjpritch25 on 2006-09-05
This is hard to explain, but i will do my best.  
When i go to write a new message i am missing this toolbar.

[IMG]http://i93.photobucket.com/albums/l51/littlegeneral25/Screenshot-Composenosubject.png[/IMG]

When i am reading new messages, i can **Right Click** on the message, choose **Edit as New** and the following toolbar will suddenly appear.  Weird.

[IMG]http://i93.photobucket.com/albums/l51/littlegeneral25/Screenshot-ComposeAGOODANSWERTOADUM.png[/IMG]
Thanks in Advance!!!!](*,) ](*,)

---

### Post by marianom on 2006-09-05
Hi, check this:
when you're writing a new message go to View-> Toolbar -> Format Tool bar
and verify if it's clicked (the menu name might be different since I'm doing a literal translation from my TB which it's in castilian).

By the way, good drawings!!

---

### Post by sjpritch25 on 2006-09-05
Okay, when i just click on **New Message**.  I only two options and these are both checked **[color=red]Mail Toolbar**[/color] and **[color=red]Status Bar**[/color].  

Now, when i click on a new message, right click on the message and click on **[color=blue]Edit as New**[/color].  Here is whats checked under **View** > **Toolbars**: **[color=blue]Mail Toolbar**[/color], **[color=blue]Formating Toolbar**[/color], **[color=blue]Status Bar**[/color].  **Formating Toolbar** is what's missing.  How i get it enabled for a **New Message**.  Don't know](*,) ](*,)

---

### Post by tminuszero on 2006-09-05
I don't know how you *did* it, but I know how to fix it. I think.

Go to: Edit > Preferences > Advanced (General Tab)
Click "Config Editor"
In the filter bar type "HTML" and hit "Enter"
There should be an item in bold that reads something like:

**mail.identity.id1.compose_html**

Currently it should be set to False. Double click to set it to "True"

I'm quite sure that this can be done in the preferences menu somewhere, but like you, I couldn't find it. Hope this works for you! :)

---

### Post by sjpritch25 on 2006-09-06
> **tminuszero said:**
> I don't know how you *did* it, but I know how to fix it. I think.

Go to: Edit > Preferences > Advanced (General Tab)
Click "Config Editor"
In the filter bar type "HTML" and hit "Enter"
There should be an item in bold that reads something like:

**mail.identity.id1.compose_html**

Currently it should be set to False. Double click to set it to "True"

I'm quite sure that this can be done in the preferences menu somewhere, but like you, I couldn't find it. Hope this works for you! :)

Thanks a bunch!!!!! \\:D/  I was going to try and dig in about:config, however, i have no idea what i am doing.  Believe it or not, I had 4 different entries because of my four accounts.  I changed for all of my accounts, it works for all and i really appriecate your help.  ;-)

---

### Post by sjpritch25 on 2007-03-25
Ok, the problem cropped up again.   However, its only on some of my emails.   Any idea why this would happen to just some????   I have i feeling that if the email doesn't have html code in it the formatting toolbar will to be available.   Any idea???   Thanks.

---

