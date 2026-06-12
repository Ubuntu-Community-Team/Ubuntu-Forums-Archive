---
title: "error editing sudoers list with visudo"
date: 2009-03-25
forum: General Help
---

### Post by chriskin on 2009-03-25
i cannot save my sudoers list while editing via visudo

in the first lines, it says that it MUST be edited with visudo
is it just a precaution to avoid mistakes or something will happen if i edit it through gedit?

:popcorn:

---

### Post by eldragon on 2009-03-25
> **chriskin said:**
> i cannot save my sudoers list while editing via visudo

in the first lines, it says that it MUST be edited with visudo
is it just a precaution to avoid mistakes or something will happen if i edit it through gedit?

:popcorn:

its a protection to a wrongly configured sudoers file, which will render sudo useless. and if you dont have a root account setup, will lock you out of the system.

always edit sudoers with visudo. anyway, post here the changes you are trying to make so that someone can point out the mistakes.

---

### Post by kanikilu on 2009-03-25
If you've already edited it in gedit (or elsewhere), you can also check for syntax errors with ```
sudo visudo -c
```

---

### Post by chriskin on 2009-03-25
i have made the same changes on my 9.04 installation and nothing is wrong, when pressing control+o , save happens , everything is ok :)

---

### Post by chriskin on 2009-03-25
> **kanikilu said:**
> If you've already edited it in gedit (or elsewhere), you can also check for syntax errors with ```
sudo visudo -c
```


does this mean that if i edit it correctly in gedit, nothing will be wrong?

ok i know that it sounds weird, but they got the huge "MUST" on top :P

---

### Post by Bachstelze on 2009-03-25
> **chriskin said:**
> does this mean that if i edit it correctly in gedit, nothing will be wrong?

Yes, but this is still a bad idea. A typo can happen anytime... If visudo complains that your file is wrong, it's for a reason.

---

### Post by chriskin on 2009-03-25
> **HymnToLife said:**
> Yes, but this is still a bad idea. A typo can happen anytime... If visudo complains that your file is wrong, it's for a reason.


i understand, but i am sure about it. it will be exactly the same as the working one on 9.04.
------------

thank you for your answers :)

---

### Post by sisco311 on 2009-03-25
The syntax check works with any editor.

To use gedit (or any other GUI editor):
```
export VISUAL=gedit && sudo -E visudo
unset VISUAL
```

To use a CLI editor, for example vi:
```
export EDITOR=vi && sudo -E visudo
unset EDITOR
```

But you have to run the commands in a terminal.

---

### Post by chriskin on 2009-03-25
> **sisco311 said:**
> The syntax check works with any editor.

To use gedit (or any other GUI editor):
```
export VISUAL=gedit && sudo -E visudo
unset VISUAL
```To use a CLI editor, for example vi:
```
export EDITOR=vi && sudo -E visudo
unset EDITOR
```But you have to run the commands in a terminal.


i would give a thanks for your answer if it was not unavailable :)

i know what i have to write though, no reason for syntax check

---

### Post by sisco311 on 2009-03-25
visudo edits the sudoers file in a safe fashion:
[list]
[*] locks the sudoers file against multiple simultaneous edits
[*] provides basic sanity checks
[*] checks for parse errors
[*] saves the file with correct permissions (0440)
[/list]

[I]is it just a precaution to avoid mistakes or something will happen if i edit it through gedit?
[/I]
yes it's a precaution.

most of the time nothing bad will happen, but some of the time will break sudo.

why would you risk?

---

