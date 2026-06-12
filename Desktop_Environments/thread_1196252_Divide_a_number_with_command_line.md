---
title: "Divide a number with command line?"
date: 2009-06-24
forum: Desktop Environments
---

### Post by SoftwareExplorer on 2009-06-24
Hi. Is there a way that I can divide a number using the command line? I want to make a script that puts out numbers from 1-100 divide those by 100 so that the result will be between 0 and 1.

Thanks in advance.

---

### Post by m_duck on 2009-06-24
I'm not sure if it is exactly what you want but command line division has just been mentioned [thread=1196252]here[/thread] in post #5.

EDIT: Heh, your thread...

---

### Post by VCoolio on 2009-06-24
I told you on the other thread about conky, lol. Run "man bc" but basically it's just piping to it.

echo "scale=1; a/b" | bc

will divide a by b with 1 decimal output.

---

### Post by SoftwareExplorer on 2009-06-24
> **VCoolio said:**
> I told you on the other thread about conky, lol. Run "man bc" but basically it's just piping to it.

echo "scale=1; a/b" | bc

will divide a by b with 1 decimal output.

Thanks:D I just asked about division in this separate thread because I thought it would be more easily found and therefore more helpful if division was in a separate thread from one about conky.

---

### Post by SoftwareExplorer on 2009-06-24
Here's how I did it: ```
echo "scale=<number-of-decimal-places>; $(<command-that-gets-the-number-you-need>)/<number-you-want-to-divide-by>" | bc -q
```

The -q option keeps bc from printing copyright notices into your script.

Hope this helps someone sometime in the future.

---

