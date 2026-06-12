---
title: "Problem removing upower"
date: 2006-01-10
forum: Desktop Environments
---

### Post by rskovacs on 2006-01-10
To try upower, I installed it following the instructions on the Ubuntu wiki, but the program doesn't seem to work...I don't care to fix that, I'd rather just have the default Ubuntu splash back, but when I go to uninstall upower (and install usplash and ubuntu-desktop) i get the following error message:

E: upower: subprocess post-removal script returned error exit status 1

during the process of uninstalling upower.  Anyone have any idea what that means and how to fix it so i can just bring Ubuntu back to normal?

EDIT: Actually, I guess I could stick with upower, assuming someone can help me with the following error.  When I boot up since having installed upower, I get a message shortly after GRUB loads that says an incorrect video setting was passed (I don't remember the exact wording) and then I have too choose one of seven choices of ROWSxCOLS, which seems to just pick a resolution, and then it just goes through a text-only boot anyway!  Which is why I want to just uninstall upower.  But if somehow I can't (even though that would make no sense) hopefully someone can help me get upower to work right, as long as I'm stuck with it.)

---

### Post by KillerBOB on 2006-01-14
Hi! I had the exact same problem when I first installed Upower (also following the [Wiki]("https://wiki.ubuntu.com/Upower")). I had issues getting it to work with my custom kernel, but that is another issue. 
I had to manually remove the startup scripts, i.e /etc/init.d/upower*. 
```
sudo rm /etc/init.d/upower*
```
After removing those scripts I could remove upower successfully with ```
sudo apt-get --purge remove upower upower-theme-ubuntu
```

I hope this helps you

---

### Post by rskovacs on 2006-01-22
it worked :) I reinstalled usplash also, now I'm about to reboot and we'll see how it goes... :)

---

