---
title: "gnome defualt spellcheck"
date: 2005-03-25
forum: Desktop Environments
---

### Post by stevenvu on 2005-03-25
Where has it gone? I used to be able to type in gaim and words got spell checked automagically, rather liked the feature. Did i turn it off by accident?

It must have vanished after an update i did. Spellcheck in open office 2 also does not work for me, i've installed the gnome gui package to i think.

---

### Post by Simian on 2005-04-10
[QUOTE=stevenvu]Where has it gone? I used to be able to type in gaim and words got spell checked automagically, rather liked the feature. Did i turn it off by accident?

It must have vanished after an update i did. Spellcheck in open office 2 also does not work for me, i've installed the gnome gui package to i think.[/QUOTE]

I have the same problem. Did you find out how to fix this yet?

---

### Post by Simian on 2005-04-11
[QUOTE=Simian]I have the same problem. Did you find out how to fix this yet?[/QUOTE]
 I guess nobody knows then?

---

### Post by jobezone on 2005-04-11
First, search for "language" in synaptic, and install your respective language package (one should be called language-support-xx , where xx is your country code. There is another that depends on the previous, I think).
This should automatically download the engines and dictionaries for spellchecking in Ubuntu.
If it doesn't, see if you have installed aspell for Gnome spellchecking, and myspell for Openoffice spellchecking, and their respective dictionary packages (both for aspell and myspell).

---

### Post by Simian on 2005-04-12
[QUOTE=jobezone]First, search for "language" in synaptic, and install your respective language package (one should be called language-support-xx , where xx is your country code. There is another that depends on the previous, I think).
This should automatically download the engines and dictionaries for spellchecking in Ubuntu.
If it doesn't, see if you have installed aspell for Gnome spellchecking, and myspell for Openoffice spellchecking, and their respective dictionary packages (both for aspell and myspell).[/QUOTE]
 Thanks Jobezone. I seem to have spell checking on a lot of applications (evolution, bluefish, etc) but not on OpenOffice 2.

In OpenOffice 2, if I go to Tools>Options>Language>Writing Aids there is nothing under Available Language Moduals. I think this is where my problem is. There doesn't seem to be any way to edit this. I've tried google but found nothing. I don't suppose you (or anyone) know how to fix this.

---

### Post by Simian on 2005-04-12
It's ok. I've found a temporary way to get the spell checker working (Though I'm sure that it's not the correct way).
I installed OpenOffice 1.1 (as I removed it before I upgraded to version 2). Now the spell checker works in OpenOffice 2.

---

### Post by Ubuntukka on 2005-06-13
Hi. I was having this same problem. I went to 
tools - options - language settings - languages 
and changed the default languages for documents to English UK.

After this, the spell checking worked.

lots of red underlined words now ! [-X

---

### Post by Mr Frosti on 2005-07-20
[QUOTE=Simian]It's ok. I've found a temporary way to get the spell checker working (Though I'm sure that it's not the correct way).
I installed OpenOffice 1.1 (as I removed it before I upgraded to version 2). Now the spell checker works in OpenOffice 2.[/QUOTE]

This solved the spellcheck problem for me in Open Office 2. It seems that version 2 somehow uses the dictionaries that are incorporated in version 1.1*.

To reinstall Open Office 1.1, type in ```
sudo apt-get install openoffice.org
```

---

