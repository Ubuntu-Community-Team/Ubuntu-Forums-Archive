---
title: "Hints to use Kate Editor with R computing and statistical enviroment"
date: 2007-06-26
forum: Education &amp; Science
---

### Post by GibaNet on 2007-06-26
Hello,

I'm a new user of Kate and I'd like to no more about functionalities to run R programs using kate.

For example, I'd like to know how to configure a command to send one line of my R program in the kate editor to run in the terminal which is with R active. And more, how do it with options to send or not the cursor to the terminal?

Gratefull for any help and I wish another hints can be send for this topic!

GibaNet.

---

### Post by akniss on 2007-06-26
> **GibaNet said:**
> Hello,

I'm a new user of Kate and I'd like to no more about functionalities to run R programs using kate.

For example, I'd like to know how to configure a command to send one line of my R program in the kate editor to run in the terminal which is with R active. And more, how do it with options to send or not the cursor to the terminal?

Gratefull for any help and I wish another hints can be send for this topic!

GibaNet.

This is not an answer to your question, but as someone who used to use Kate for R script editing it sounds like you would be happier with ESS/emacs.  It can be installed with
```
sudo aptitude install ess
```
Check it out.  I think you will find it has the functionality you are after, and is rather addictive once you learn the keystrokes.
[http://www.math.montana.edu/stat/tutorials/ESS.html](http://www.math.montana.edu/stat/tutorials/ESS.html)

---

### Post by mayeulk on 2011-05-06
You can use autokey to automate a key sequence that will ask kate to do this.
See [http://en.wikipedia.org/wiki/Autokey](http://en.wikipedia.org/wiki/Autokey)
and download or see how to install here:
[http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)
(Ubuntu and Debian packages available).

The macro that I use successfully with R:

```
# To send a multiline block (no line feed) under kate in R,
# the cursor being anywhere in the line, word wrap activated
# (max 4 lines):
# in kate, configure two shortcuts (Menu "settings" "configure
shortcuts") for "Pipe to terminal":
# win + C (mandatory, will be used by this macro)
# win + something else (optional, to ask kate Pipe to terminal without
using this
# In autokey, define ctrl+< as the shortcut to execute this macro


# select all
keyboard.send_keys("<home><home><home><home><shift>+<end><shift>+<end><shift>+<end><shift>+<end><shift>+<right>")

# pipe to terminal
# keyboard.send_keys("<ctrl>+>")
keyboard.send_keys("<super>+C")

keyboard.send_keys("<shift>+<left>")


# to see autokey config if not visible in icon: autokey -c
```

---

### Post by earlycj5 on 2011-05-07
The easier(est?) way for Kate/R integration is RKWard, no?

---

