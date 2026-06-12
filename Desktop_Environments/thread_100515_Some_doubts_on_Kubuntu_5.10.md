---
title: "Some doubts on Kubuntu 5.10"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Rochvellon on 2005-12-07
Good evening (or morning :rolleyes: )!
I've just installed Kubuntu 5.10 and I'm loving it! I've just configured my internet connection and now I'm onto more important things:
[LIST=1]
[*]I would like to know how I can read my NTFS partition, which has Windows XP SP2 on it. I keep getting a message telling me I don't have the rights to access that.
[*]And I would like to know how can I write in directories like /usr/bin/
[*]I would like to use Firefox instead of Konqueror. I've downloaded the file and unpacked it according to the official site's instructions, but I don't know which file to click to start it.
[*]Is there a default application folder in Kubuntu? Like "Program files" on Windows... I think it's /usr/bin/, but, as you can notice, I can't write to that folder.
[*]I also wish to know if there's a way to make Windows the default choice when GRUB prompts you for the OS in my computer's boot. I'm aware that you can do that in Mandriva, so I would like instructions on how to do that in Kubuntu.
[*]How can I add apps that I installed (e.g. Firefox) to the "Start Menu" (dunno what's the right name)?
[/LIST]

Thank you!

---

### Post by r3m0t on 2005-12-07
>    1. I would like to know how I can read my NTFS partition, which has Windows XP SP2 on it. I keep getting a message telling me I don't have the rights to access that.
   2. And I would like to know how can I write in directories like /usr/bin/
   3. I would like to use Firefox instead of Konqueror. I've downloaded the file and unpacked it according to the official site's instructions, but I don't know which file to click to start it.
   4. Is there a default application folder in Kubuntu? Like "Program files" on Windows... I think it's /usr/bin/, but, as you can notice, I can't write to that folder.
   5. I also wish to know if there's a way to make Windows the default choice when GRUB prompts you for the OS in my computer's boot. I'm aware that you can do that in Mandriva, so I would like instructions on how to do that in Kubuntu.
   6. How can I add apps that I installed (e.g. Firefox) to the "Start Menu" (dunno what's the right name)?

1. Please open /etc/fstab in a text editor and paste in the contents.
2. If you ever need to write to a system directory (and you really should know what you are doing) you need to run your text editor/hex editor/file manager with "sudo". This elevates your privileges to the system administrator for that program on that time. So you can go to konsole and type "sudo kate". It will ask you for your password (just the one you use to login when you switch on the computer) and then open kate and let you edit anything.
As an aside: the following directories are *not* system directories: /home/<username> and /tmp/. Most other areas are for the system.
3. Because every Linux distribution works a little differently, you need to download a package which is just for Ubuntu instead of the package which the Mozilla (Firefox) team make. Luckily for you there is a central place for all your Kubuntu (and Ubuntu) packages (quite sensibly called the repository) and a program to help you navigate it. The program is Adept, and you can read about how to use it at [http://kubuntu.org/docs/kquickguide/C/ch02s07.html](http://kubuntu.org/docs/kquickguide/C/ch02s07.html)
*(edit: just in case you didn't realise, the package is called "firefox" or something similar)*
After you install Firefox from Adept, you then need to rummage around your KDE settings to make it your default browser - that means that if you click on a link in Kopete or Konversation (instant messaging or chatrooms) Firefox will open up.
4. There are plenty, but I need to know why you care - what would you do with those folders?
5. I can reply to this better from my Kubuntu system, but I assure you it's possible. ;)
6. The packages you get using Adept do that automatically.

---

### Post by aysiu on 2005-12-07
I wrote a PDF that answers just about every one of your questions in great detail: [http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf)

---

### Post by Rochvellon on 2005-12-07
Thank you both very much!

---

