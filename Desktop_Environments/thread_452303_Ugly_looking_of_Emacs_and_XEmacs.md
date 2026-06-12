---
title: "Ugly looking of Emacs and XEmacs"
date: 2007-05-23
forum: Desktop Environments
---

### Post by ryukocn on 2007-05-23
I am using Ubuntu 6.10 and I have thought Emacs should be looking elegant like it under fedora or centos. But I am disappointed after I installed it. The font of menu is to large. And the default font is ugly. I have tried XEmacs too, same situation happens. The worst thing is I don't know much about Emacs Customization. 

Does anyone have the same situation with me?

---

### Post by onbongos on 2007-05-24
there is a emacs-gtk or emacs-gnome package available that improves the look somewhat

---

### Post by Lux Perpetua on 2007-05-24
Yes, there those are options. There's also a Howto around here on installing Emacs with antialiased fonts (a search will turn it up). 

Also, you can specify the font you want on the command line via -fn: ```
emacs -fn "-*-courier-medium-r-*-*-12-*-*-*-*-*-*-*"
```I think the "-fn" option is available to most X-windows applications. If you're not sure how to name your font, you can run ```
xfontsel
```and pick one you like.

---

### Post by penvzila on 2007-06-22
I found nothing that worked on ubuntuforums.  However, I was able to get GNU Emacs with smooth fonts by following these instructions:

[http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs](http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs)

---

### Post by pvdg on 2007-06-26
I have the opposite problem: after upgrading to edgy and then feisty, the fonts in the emacs menu are too small. I know how to change the buffer fonts size (they were also too small), but I'm not sure about the menu, even after reading the manual. Any tips? I don't want to install another version of emacs, just customize the default version in feisty.

---

### Post by alex-v on 2007-08-22
In order to adjust menu/popup fonts used by (X)Emacs you need to set up appropriate X resources. For instance, put the following into your ~/.Xresources file (assuming you have Arial font):

```

Emacs*menubar*fontSet: -*-arial-medium-r-*-*-*-120-*-*-*-*-*-*
Emacs*menu*fontSet: -*-arial-medium-r-*-*-*-120-*-*-*-*-*-*
Emacs*popup*fontSet: -*-arial-medium-r-*-*-*-120-*-*-*-*-*-*

```

then reload the file

```

xrdb -load ~/.Xresources

```

and restart XEmacs.
[http://www.xemacs.org/FAQ/index.html]("http://www.xemacs.org/FAQ/index.html")

---

