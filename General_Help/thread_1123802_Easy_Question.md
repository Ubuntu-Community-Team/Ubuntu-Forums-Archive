---
title: "Easy Question"
date: 2009-04-12
forum: General Help
---

### Post by Trafficflow on 2009-04-12
I am new and I am still learning. I am determined to learn on my own but I get stuck every so often. I am trying to use the command lsusb  grep natsemi. What does the line stand for in the center? How do you put it in?

---

### Post by Toshubu on 2009-04-12
I think you're talking about the "|" symbol. I think they call it a pipe symbol; and it is the upper case (shift) version of the backslash (\) key, on a standard us keyboard. I would think-in the context you're using, the command would be: lsusb | grep natsemi.

---

### Post by Trafficflow on 2009-04-12
Thanks. That was it.

---

### Post by suavecu on 2009-04-12
That is the case. And what it does is send the output to another program. So in this case when you are running lsusb, normally the output is just sent to terminal for you to see. When you pipe it to grep (use the |) it send the output to the grep program, which then searches for a particular string and prints the lines that have that string to your terminal.

---

