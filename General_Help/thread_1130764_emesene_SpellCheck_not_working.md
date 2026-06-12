---
title: "emesene SpellCheck not working"
date: 2009-04-20
forum: General Help
---

### Post by Mr Tim on 2009-04-20
Hello

I've been playing around with emesene, considering whether it's worth switching from pidgin, and at the moment I'm really liking it. The only problem is I've been unable to get the "Spell" plugin working, and spellcheck is something which I consider to be an essential feature.

When I try to enable the plugin it comes up with the following error:
    "Error applying Spell to input (enchant error for language: ) Plugin disabled"
I have the unfortunate feeling that I am missing something very simple (I tend to do that a lot), and any help would be appreciated.

Thanks in advance.

---

### Post by JeyPeyy on 2009-05-28
I have the same problem. Anyone knows how to fix this?

---

### Post by matrixblue on 2009-06-06
Type "sudo apt-get install python-gnome2-extras" and restart emesene

---

### Post by pjalegria on 2009-06-17
How can i add PT language support???
thanks

---

### Post by monikgtr on 2009-07-21
If package "sudo apt-get install python-gnome2-extras" is already installed, just restart Emesene.

thanks!

---

### Post by MockY on 2009-08-02
Before I installed python-gnome2-extras the error was different, saying that I needed to install gtkspell. By installing python-gnome2-extras, the error message changed into the error this thread is about. Even after a computer reboot the error remained. 
So is there any other packages missing that needs to be installed?
Using 8.10 Intrepid Ibex.

---

### Post by matrixblue on 2009-08-02
> **MockY said:**
> Before I installed python-gnome2-extras the error was different, saying that I needed to install gtkspell. By installing python-gnome2-extras, the error message changed into the error this thread is about. Even after a computer reboot the error remained. 
So is there any other packages missing that needs to be installed?
Using 8.10 Intrepid Ibex.

Gtkspell is installed in addition to python-gnome2-extras right?

---

### Post by MockY on 2009-08-02
> **matrixblue said:**
> Gtkspell is installed in addition to python-gnome2-extras right?

I assume so since you can't install it separately. Regardless, python-gnome2-extras did not fix it for me.

---

### Post by SuperMau on 2009-08-14
I had the same problem until I selected preferences button of the plugin and picked my language...

Cheers

---

### Post by Eyeron on 2009-09-23
had the same problem. thanks fellas
solved now, oui?

---

### Post by frasten on 2009-10-03
To solve this issue, run this command:

```
nautilus ~/.config/emesene1.0/
```

Then enter your profile folder (mine is *username_gmail_com*),
and create a new empty file, call it **Spell.conf**, and put this text inside:
```
lang=en
```

or **it** for italian, etc.

Save and re-run emesene.

---

### Post by sensory on 2009-10-27
Thanks Frasten, that worked like a charm!

---

### Post by MockY on 2009-12-26
It sure did work. Thanks.

---

