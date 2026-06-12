---
title: "run R with gedit"
date: 2010-05-22
forum: Education &amp; Science
---

### Post by santiagorf on 2010-05-22
Hi all,
I have installed the plug-in to run R code Everything is fine, except  for one thing.

When I run a code such as:

```
a<-3
cat(a ,"\n")
```

I get as a result:

```

1> cat(a ,"\n")
3

```

But I would like to have the following as a result:
```
3
```

That is, a cleaner output.

Does anyone knows how to solve it?

Thank you,
Santiagorf

---

### Post by Axolotl9250 on 2010-05-25
Hi there, I'm about to investigate the plugin myself, I'm always looking for new ways to use R to share with my stats tutor. I wondered if you'd seen this page [HTML]http://ubuntuforums.org/showthread.php?p=9356375#post9356375[/HTML] I know the method that [knattlhuber]("http://ubuntuforums.org/member.php?u=468237") suggested works with me and its easy, however I have found it works better if I send the whole lot rather than line by line (where I get a few errors) so it's good for running a bit of code and seeing how it turns out. A good more heavy duty option is using Emacs with ESS, have you used this? I personally like it a lot and it definitely has more features than gedit. For me, when I downloaded Emacs 23, I can use ESS by creating or loading an .R file and the option to bring up an ESS buffer working as a live R console came up automatically without the need for installing additional packages and such. After I've had chance to have a play with the gedit plug-in tonight I'll come back and share my experience (or lack of if it doesn't work) with it.

---

### Post by Axolotl9250 on 2010-05-25
Ah right, I just had a go at using the plugin, it happened to me as well. The only explanation I can give is that it's a live R console and in all R consoles even the EMACS ESS buffer window, it shows you the command you just entered and then the result. In all the text editor's I've used its been like this with emphasis on keeping the script you're writing clean for reproducible research, as opposed to giving a clean output - although I too would like a clean output! It may be worth investigating if there is an option to put in the code to turn echo off, this can be done in LyX with Sweave so as when writing a document, in my case a research paper and you're describing the results, it gives the ouptut of R on the document but none of the commands typed in.

---

### Post by santiagorf on 2010-05-25
Hi Axolotl9250,

I'll keep looking for an alternative, and if I find it, I'll post it.
So far, a solution is to read the program by using 

```
source("path..")
```

but it's not very elegant...

---

