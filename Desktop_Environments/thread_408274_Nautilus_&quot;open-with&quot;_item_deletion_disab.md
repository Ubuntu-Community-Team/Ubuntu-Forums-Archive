---
title: "Nautilus &quot;open-with&quot; item deletion disabled"
date: 2007-04-13
forum: Desktop Environments
---

### Post by Unconscious on 2007-04-13
I'm pretty happy, in general, with my edgy desktop installations, however...

I want to change the default applications that certain file types are opened by. 

For instance; I don't like gedit (mercifully, I won't go into that here). I use Vim. I never use gedit. Yet, there appears to be no way to remove gedit from the "open-with" choices. I can add Vim to the list of apps in the "open-with"dialog, but I cannot remove gedit. The "remove" button is grayed out.

Why is this so difficult?

---

### Post by ComplexNumber on 2007-04-13
> **Unconscious said:**
> I'm pretty happy, in general, with my edgy desktop installations, however...

I want to change the default applications that certain file types are opened by. 

For instance; I don't like gedit (mercifully, I won't go into that here). I use Vim. I never use gedit. Yet, there appears to be no way to remove gedit from the "open-with" choices. I can add Vim to the list of apps in the "open-with"dialog, but I cannot remove gedit. The "remove" button is grayed out.

Why is this so difficult?
the reason why it can't be changed is because that information is owned by root.  the other entries that you can change exist in ~./local/share/applications. because those that are entered by you are held in your home directory, they can be changed. the chance are, the file association that you can't change was added when you first installed the application.
go in the following directory and look for the application (ie gedit). edit the file to delete the mime type that you don't want associated with that application. for example, if you don't want exaile to open mp3 files, then go to Exaile in the directory below and delte the mp3 mime type  entry:
[B]/usr/share/applications



[/B]btw if at any time in the future you believe that you are likely to change a lot of mime types that are associated with various applicastions, you can always install an aplication called assoGiate. you can get it from [here]("http://gnomefiles.org/app.php/assoGiate").

---

### Post by HolyJoe on 2007-04-13
It's good. thanks.

---

### Post by Unconscious on 2007-04-13
Thanks for your response. 

I did as suggested:

    *sudo vi /usr/share/applications/gedit.desktop* (it was the only entry for gedit)

...deleted the only line that referred to the mime type text/plain. 

I still couldn't remove gedit from the "open with" dialog. 

I then shutdown and rebooted. Still no joy. 

...So I downloaded assogiate, as suggested, and built it. (I had to install lots of libraries). It works, but I don't see how editing the file type description will help me dissociate gedit from text files.

Again, I don't see why this has to be soooo difficult. (This is something that users do all the time in M$ win.)

:confused:

---

### Post by ComplexNumber on 2007-04-13
oh well, it worked for me. 

thats correct. i got my logic wrong when i mentioned about the file type editor. 

try the solution [here]("http://ubuntuforums.org/showthread.php?t=391233").

---

