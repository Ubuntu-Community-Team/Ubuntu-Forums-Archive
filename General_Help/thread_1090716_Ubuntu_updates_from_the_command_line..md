---
title: "Ubuntu updates from the command line."
date: 2009-03-08
forum: General Help
---

### Post by robfindlay on 2009-03-08
I've just switched to Fluxbox--slow machine here. And without the gnome panel app that alerts you to Ubuntu updates is there a way to check and execute the update from the command line? 


Thanks!

-Rob

---

### Post by whoop on 2009-03-08
sudo apt-get update
sudo apt-get upgrade (or) sudo apt-get dist-upgrade

---

### Post by Scar-face on 2009-03-08
sudo apt-get update (updates your sources)
sudo apt-get upgrade (checks if the installed version of all you programs is the newest. If there is a newer one, it will update.)

---

### Post by zvacet on 2009-03-08
All in one line

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by robfindlay on 2009-03-08
> **zvacet said:**
> All in one line

```
sudo apt-get update && sudo apt-get upgrade
```

Now, would the following work in a bash script?

exec sudo apt-get update &&
exec sudo apt-get upgrade

I've made the text file and set it chmod a+x 


-Rob

---

### Post by Slim Odds on 2009-03-08
> **robfindlay said:**
> Now, would the following work in a bash script?

exec sudo apt-get update &&
exec sudo apt-get upgrade

I've made the text file and set it chmod a+x 


No need for exec and combine the lines....

---

### Post by robfindlay on 2009-03-08
> **Slim Odds said:**
> No need for exec and combine the lines....

Is there a way to force a pause between each?  As I'm a lock error as one command hasn't released the database to the next.

---

### Post by Slim Odds on 2009-03-08
> **robfindlay said:**
> Is there a way to force a pause between each?  As I'm a lock error as one command hasn't released the database to the next.

If you combine the lines, the second command will run **after** the first.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by robfindlay on 2009-03-08
> **Slim Odds said:**
> If you combine the lines, the second command will run **after** the first.

```
sudo apt-get update && sudo apt-get upgrade
```

That did it!

I need to dig out my shell scripting cookbook from the "old days" of slackware :-)

---

### Post by Slim Odds on 2009-03-08
> **robfindlay said:**
> I need to dig out my shell scripting cookbook from the "old days" of slackware :-)

I find this very handy: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

