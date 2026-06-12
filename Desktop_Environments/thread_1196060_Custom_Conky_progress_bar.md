---
title: "Custom Conky progress bar?"
date: 2009-06-24
forum: Desktop Environments
---

### Post by SoftwareExplorer on 2009-06-24
Hi. I have a script that will return a number that is the percent done of the current folding at home unit. so, for example, if I do ```
/home/bjorn/.foldpercent.sh
``` I might get something like ```
 6 
``` back. Is there a way to put this as a progress bar in conky?

---

### Post by Ape3000 on 2009-06-24
I've been looking for a similar thing for my temperatures and net speeds.

---

### Post by SoftwareExplorer on 2009-06-24
By the way```
${execbar /home/bjorn/.foldpercent.sh}
``` just gets me a bar that is at 100%.

---

### Post by SoftwareExplorer on 2009-06-24
Ok, I think I found half of the answer. [It's here.]("http://ubuntuforums.org/showthread.php?p=5996117#post5996117")

However, now I need to know how to divide on the command line.

---

### Post by VCoolio on 2009-06-24
Interesting. Well, piping to bc does a lot.
```
echo "scale=1; 50/100" | bc
```

gives output .5
scale means number of decimals. Man bc tells more.

---

### Post by SoftwareExplorer on 2009-06-24
> **Ape3000 said:**
> I've been looking for a similar thing for my temperatures and net speeds.

From what it says [here]("http://ubuntuforums.org/showthread.php?p=5996117#post5996117"), execbar takes a number between 0 and 1.

So, if you look at the thread I started [here]("http://ubuntuforums.org/showthread.php?p=7512269#post7512269"), it will explain how to setup division in a command. Then you can use it to make temperatures and net speeds go into a bar because current reading (of temperature for example) divided by Max will always be between 0 and 1.

If you need more help, just tell me--I'm feeling confident now that I got it working for me.

For anyone who is interested, here is the folding at home part of my .conkyrc

```
Folding at Home:
${color red}${execi 15 cat /opt/foldingathome/1/FAHlog.txt | tr '(' '\n' |tr ')' '\n' | grep -E "(%|percent)"|tail -n 1 | tr  -d 'percent'  | tr  -d '%'} %  ${execbar echo "scale=2; $(cat /opt/foldingathome/1/FAHlog.txt | tr '(' '\n' |tr ')' '\n' | grep -E "(%|percent)"|tail -n 1 | tr  -d 'percent'  | tr  -d '%')/100" | bc -q}
```

---

