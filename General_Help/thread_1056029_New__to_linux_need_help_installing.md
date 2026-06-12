---
title: "New  to linux need help installing"
date: 2009-01-31
forum: General Help
---

### Post by nesto1000 on 2009-01-31
I need help installing java on my computer... i am fairly  new to linux just installed it yesterday. i want java for online games, i have tried installing it don't know how... 

i appreciate your time for reading this

---

### Post by ChildOfMana on 2009-01-31
Try [here]("http://savethegirhogs.blogspot.com/2009/01/few-things-to-do-post-installation.html"). The second point. It will install support for restricted Codecs and for Flash and Java as well.

---

### Post by nesto1000 on 2009-01-31
hmmm... i pasted the stuff on the terminal but nothing seems to happen...

---

### Post by taurus on 2009-01-31
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
When you get to the java license screen, hit the Tab key to highlight the <OK> and Return key to accept it.

---

### Post by nesto1000 on 2009-01-31
hmmm well i have already installed java from the add/remove programs place... but I cant use it on firefox...

---

### Post by jmszr on 2009-01-31
nesto1000,
          I would suggest to any new user that they read this: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php) - it a most excellent beginner's guide and should take care of your present problem. Also you can go to Applications > Add/Remove > Show: All Available Applications > Search: Java > Click on Java (including Ubuntu Restricted Extras) and Apply.

Edit: Do you happen to have Noscript enabled on Firefox?

---

### Post by nesto1000 on 2009-01-31
i did search for java... and i did install it... i will take a look at that website...

---

### Post by taurus on 2009-01-31
Make sure you restart firefox.  Then in the address field, type

```
about:plugins
```
and see if java plugin is on the list and what version.

Also, what is the output of this command from a terminal?

```
java -version
```

---

