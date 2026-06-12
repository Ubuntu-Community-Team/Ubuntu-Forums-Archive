---
title: "Change prompt"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-02
I would like to change the prompt that appears in the console:

> admin@admin-desktop:

Because it's too large, with a new one like this:

> admin@admin:

Is it possible?

---

### Post by karlsson88 on 2006-07-02
i think "admin-desktop" is your computers name? you can change hostname, but it isn't always good to do that.

---

### Post by jimbob on 2006-07-02
There is an environment variable named PS1 that sets this up.

In your home account make a backup copy of the file .bashrc in case something goes wrong.

In .bashrc look for the first line that looks like this:

   PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

If you edit that line to look like this:

PS1='${debian_chroot:+($debian_chroot)}\$ '

 then all you will have for a prompt is the $ sign.  You can experiment with the \u@, \h: and \w as you wish to get what you want.  Make a change and then open a new terminal window and observe the effect.

Have fun.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by pt78 on 2006-07-02
And some other examples (some are really great) can be found here: [http://www.dreaming.org/~giles/bashprompt/prompts/](http://www.dreaming.org/~giles/bashprompt/prompts/)

---

