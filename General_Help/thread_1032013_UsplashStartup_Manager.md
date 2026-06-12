---
title: "Usplash/Startup Manager"
date: 2009-01-05
forum: General Help
---

### Post by doubad on 2009-01-05
I installed startup manager so i could easily switch between usplash themes. When I switch to any theme other than the default, I get a black/text loading screen. I've tried with about 5 different themes so far.
I'm running intrepid.

---

### Post by Secret Neo on 2009-01-06
Ya man I'm doin the exact same thing man, i wanna figure it out too.

---

### Post by doubad on 2009-01-07
I guess we may not have much help on this one

---

### Post by chamber on 2009-01-07
Have you made sure that only one is selected?

Can you post a screenshot of the startup manager so we can see the settings?

---

### Post by doubad on 2009-01-07
[http://tinypic.com/view.php?pic=2qnxt9z&s=5](http://tinypic.com/view.php?pic=2qnxt9z&s=5)

---

### Post by chamber on 2009-01-07
When installing mine I went to System>Preferences>Splash Screen and installed it from there.

---

### Post by doubad on 2009-01-07
I don't have that option on either computer.

---

### Post by chamber on 2009-01-08
Are you on hardy or intrepid?

---

### Post by fredde74 on 2009-01-08
I have the same problem.

When I run :
```
sudo usplash -c
```

I recive an error saying something like:
"No valid theme for 1024x768"

Even though I know the theme has this resolution.

Regards, Fredrik

---

### Post by Excedio on 2009-01-08
[QUOTE=chamber]Are you on hardy or intrepid?[/QUOTE]

The first post says...

[QUOTE=doubad]I'm running intrepid.[/QUOTE]

;)

---

### Post by doubad on 2009-01-08
> **fredde74 said:**
> I have the same problem.

When I run :
```
sudo usplash -c
```

I recive an error saying something like:
"No valid theme for 1024x768"

Even though I know the theme has this resolution.

Regards, Fredrik
 
I tried that and got

usplash: can't get console font: Invalid argument

---

### Post by fredde74 on 2009-01-08
> **doubad said:**
> I tried that and got

usplash: can't get console font: Invalid argument

I always get that error, even with the default ubuntu splash which works as it should. So I don´t think that is the reason why it doesn´t work.

---

### Post by Orlsend on 2009-01-08
If you are desperate for your upslpash to work you can use the project [Epidermis]("http://epidermis.tuxfamily.org/"), you can download the upsplash from the repo (Epidermis repo) and then it will install them for you. (Or your custom one which need to be ported)

---

### Post by Orlsend on 2009-01-08
sorry double cache post...

---

