---
title: "mei_me connect/disconnect timeout"
date: 2013-10-27
forum: Desktop Environments
---

### Post by atomicspin on 2013-10-27
I just upgraded to 13.10 and, once I login, the wallpaper just comes up and stays there, no menu, desktop items, etc.

When I go in to terminal, I get "mei_me (bunch of numbers): reset: connect/disconnect timeout."  

Any ideas?

---

### Post by atomicspin on 2013-10-29
Bump

---

### Post by dentaku65 on 2013-11-02
Try

ctrl+alt+f1 to open a virtual console
Then
```
sudo /etc/init.d/lightdm stop
```
Then
```
rm -R ~/.cache/sessions/
```
Reboot

---

### Post by atomicspin on 2013-11-03
Did this and it still shows the same thing after reboot.

Also, when I'm logging in to the GUI, after login, it just sits at the wallpaper screen.  Nothing else.  Related?

---

### Post by dentaku65 on 2013-11-06
Can you post the content of this?

```
cat ~/.xsession-errors
```

---

### Post by atomicspin on 2013-11-08
Here goes:

: connect to britty at :0
: for cjkv started at run_im.
: for default started at run_im.


Also, the commands you gave me did stop the ongoing error message.  Now it just sticks after I type in the password at the login screen.  Stays on the wallpaper forever. 

Thank you!

---

### Post by remusc on 2014-03-30
In fact you have 2 problems (I don't know if they are related):
(1) with the mei-me connect/disconnect (that I have also - and I am looking to solve it)
(2) Freeze desktop - related to Video drivers/Compiz etc -- you can find the solution here
[http://askubuntu.com/questions/285779/after-upgrading-to-13-04-unity-interface-is-not-showing]("http://http://askubuntu.com/questions/285779/after-upgrading-to-13-04-unity-interface-is-not-showing")

Try to solve first (2). I succeced and now I am looking solving (1)

Regards.

---

### Post by bapoumba on 2014-04-01
About #1, may be here : [https://bbs.archlinux.org/viewtopic.php?id=168403](https://bbs.archlinux.org/viewtopic.php?id=168403)

---

