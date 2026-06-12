---
title: "how do i rename keyboard layouts?"
date: 2009-01-10
forum: General Help
---

### Post by chriskin on 2009-01-10
i would like to know if there is a way to change what is shown at the keyboard indicator applet on my panel.

for example, instead of USA i would like to have AG (short for "agglika" meaning "english" in greek) and instead of Gre i would like to have EL (short for "ellinika" meaning "greek" in greek)

:popcorn:

---

### Post by chriskin on 2009-01-31
can someone help me please?
all i need is to know is the name of the file that the languages are saved, most probably :S

---

### Post by Yumi on 2009-01-31
Posted a new threat before I found yours. Am looking for the same solution. Published the solution before by editing xorg.xml. But now this file has changed. Hopefully someone knows where to edit now.

Michael

---

### Post by simosx on 2009-02-13
Indeed, the file is
/usr/share/X11/xkb/rules/xorg.xml

However, when you use a localisation (instead of US English), the name is picked from the /usr/share/locale-langpack/LL/LC_MESSAGES/xkeyboard-config.mo file.
You can decompile the file with 'msgunfmt', make change, then compile back again with 'msgfmt'. 

Hope this helps.

---

### Post by chriskin on 2009-02-14
Euxaristw polu :)



[U]Edit : it didn't seem to work :S

do i have to do something different than just rename the "USA" and "Gre" words in the text?[/U]

---

