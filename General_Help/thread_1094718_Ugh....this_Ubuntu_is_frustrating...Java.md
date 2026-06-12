---
title: "Ugh....this Ubuntu is frustrating...Java ?"
date: 2009-03-12
forum: General Help
---

### Post by Racnnut on 2009-03-12
I am trying to download and install Java on my system and everytime I try to go to the termimal to do all the instructions they provided, I get authorization errors or location errors.  Is there any simple way to install this program without going thru hoops?  

When I go to the terminal, I will type in su and then I type in the password that I thought was correct and I get an authenication error.  How do I know I have the right password.  I'm using the one I use to start the system.

---

### Post by OutOfReach on 2009-03-12
Ubuntu doesn't have a root password by default so using 'su' won't work.
Use 'sudo' and then type a command. For example:
```

sudo apt-get update

```

---

### Post by taurus on 2009-03-12
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Racnnut on 2009-03-12
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

Thanks for your input.  That worked.  Soon as I figure out the terminal and all the terminology that goes with it I think I might actually get the hang of this...:-)

---

