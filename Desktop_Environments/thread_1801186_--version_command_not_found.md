---
title: "--version command not found"
date: 2011-07-10
forum: Desktop Environments
---

### Post by kirthi on 2011-07-10
I am using ubuntu 10.04. I want to know which gnome version i am using. If i use "gnome --version" in terminal it says
"gnome: command not found"
What should I do??

---

### Post by matuskap on 2011-07-10
u can use ```
gnome-about
```

Edit: if u want it to be shown directly in terial use ```
gdm --version
```

---

### Post by kirthi on 2011-07-10
Thanks.. I am using gnome 2.30.2. If I change it to KDE what is the big difference I will find?

---

### Post by kirthi on 2011-07-10
When I used gdm --version I got this.. What it means??

** (gdm-binary:2537): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.61" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2537): WARNING **: Could not acquire name; bailing out

---

### Post by matuskap on 2011-07-10
Well obvious change will be in graphic interface. I always used Gnome but i think if u switch, u should also start using programs using KDE libraries for better performance like Amarok instead of Rhytmbox, etc...

Edit: about that WARNINGs, mby try ```
sudo gdm --version
```
P.S.: i just had the same message when i mistyped the command like --versio

---

