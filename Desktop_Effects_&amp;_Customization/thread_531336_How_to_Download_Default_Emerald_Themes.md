---
title: "How to Download Default Emerald Themes"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by dannymichel on 2007-08-21
Ubuntu Gutsy:

When I click System>Preferences>Emerald Theme Manager>Fetch GPLd Themes>Fetch Non-GPLd Themes I get a flash and nothing happens (The themes aren't there)

All I want is Rezlooks (The plain old ones that come with the thing)
Can anyone help me out?
Maybe tell me WHY this is happening and or WHERE to download Rezlooks?

---

### Post by gn2 on 2007-08-21
Here they are: [http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

---

### Post by kansei on 2007-09-20
To get the fetch buttons working, install the 'subversion' package and its dependencies. 

Directly above the fetch buttons there is text explaining this. I always forget myself the first time I try to use those buttons.

---

### Post by joske on 2007-09-22
I have subversion installed (need it for work, so I know it works), but the buttons don't do anything for me...

Anything else I'm missing?

---

### Post by joske on 2007-09-22
I used the comment on the button (svn ls), and after accepting the certificate, I was able to download non-gpl themes.

---

### Post by kansei on 2007-09-22
But the GPL ones still don't work? They don't work here either.. but the button actually does something with subversion installed. I just hadn't bothered to check the logs to see why it still wasn't working.

---

### Post by nikoPSK on 2007-09-23
I just installed gutsy (took a loooooong time, I suggest you guys wait). And I t wants emerald so:

```
sudo apt-get install emerald
```

I've intalled it.. But no themes! I've clicked on both "fetch themes" buttons but no themes yet.

---

### Post by tech9 on 2007-12-06
> **nikoPSK said:**
> I just installed gutsy (took a loooooong time, I suggest you guys wait). And I t wants emerald so:

```
sudo apt-get install emerald
```I've intalled it.. But no themes! I've clicked on both "fetch themes" buttons but no themes yet.

try 

```
 sudo apt-get install subversion 
```

buttons will work after the dependency package is installed

---

