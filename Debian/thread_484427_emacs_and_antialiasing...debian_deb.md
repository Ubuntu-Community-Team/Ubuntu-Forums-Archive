---
title: "emacs and antialiasing...debian deb?"
date: 2007-06-25
forum: Debian
---

### Post by neoflight on 2007-06-25
IS there a way i ca get debian deb for emacs with antialiasing enabled? i mean a single deb file _ dependency installation without any compiling and patching? 

i am aware of the threads on ubuntu....
if anyone of you have a deb on emacs+xft fonts enabled could you share it?

---

### Post by neoflight on 2007-06-27
Got emacs with xft enabled from the repos given below...temporarily enabled and done! the one in the apt/edgy package didnt work for me...

Here is the [link to the original ]("http://g33k.wordpress.com/2006/11/06/gnu-emacs-with-xft-goodness/")howto

```
deb http://people.ubuntu-in.org/~ghoseb/apt/ dapper main
deb-src http://people.ubuntu-in.org/~ghoseb/apt/ dapper main # for source

```

```
sudo apt-get install emacs-snapshot-gtk
```

Then added this to .emacs file in the home directory. If it does not exist then create one...

```
(set-default-font "Bitstream Vera Sans Mono-11")
```
including the brackets...... '(' and ')'

for the eager ones... here is my complete .emacs file.
BTW, i do not know how the file works or the couple of lines (other than the ones that look like comments...) in there make any differences..

[PHP](custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "rfc1345")
 '(global-font-lock-mode t nil (font-lock)))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 )
(set-default-font "Bitstream Vera Sans Mono-11")
[/PHP]
change the fonts or size as you please...

Then created a launcher with command
```
emacs-snapshot-gtk --enable-font-backend
```
or start emacs with that command from the CL.

hope this helps someone...

---

### Post by alexeys on 2007-06-30
Also there is xft-enabled Emacs 23 (although this is alpha version and highly experimental), you may be interested to look here:
[http://peadrop.com/blog/2007/01/06/pretty-emacs/](http://peadrop.com/blog/2007/01/06/pretty-emacs/)

Link to repository:
deb [http://debs.peadrop.com](http://debs.peadrop.com) feisty backports
deb-src [http://debs.peadrop.com](http://debs.peadrop.com) feisty backports

---

### Post by neoflight on 2007-07-03
Thanks..

I did not know about this...

---

### Post by tgaref on 2007-07-24
Thanks for your posts. The anti-alias fonts in emacs look great.
The only problem I have is that now the greek fonts look worse
than before. Any idea how to fix this?

thanks

---

