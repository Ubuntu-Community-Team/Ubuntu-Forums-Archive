---
title: "replace xfwm with openbox"
date: 2012-07-08
forum: Desktop Environments
---

### Post by psauxw on 2012-07-08
Hello everyone!,

I've been happy with xfce4 and xdm so far but I want to try openbox and I'm getting stuck at some point.

I tried to replace my xfwm with openbox doing
sudo apt-get remove xfwm4
sudo apt-get install openbox

everything is working exept i cant move and resize windows while in openbox.

Any help would be gladly appreciated!

Thanks for your time!

---

### Post by psauxw on 2012-07-08
come on 40 views and no replies :(

---

### Post by 3Miro on 2012-07-08
"remove" uninstalls a program, this is now what you want. You probably removed xfwm4 and now you don't have WM. Install xfwm4 back:
```
sudo apt-get install xfwm4
```

If you want to try OpenBox under XFCE, then you should use the command:
```
openbox --replace
```

You will have both xfwm4 and OpenBox and the --replace command will switch between them on-the-fly.

---

### Post by psauxw on 2012-07-09
thanks i finally went ahead and reinstalled xfce4 from a ubuntu-desktop iso instead of a mini iso (30mb) and did openbox --replace.

saved session so now openbox is the default WM.

Thanks for your help.

---

