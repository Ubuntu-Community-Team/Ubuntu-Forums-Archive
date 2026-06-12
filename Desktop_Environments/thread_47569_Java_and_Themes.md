---
title: "Java and Themes"
date: 2005-07-09
forum: Desktop Environments
---

### Post by john deere on 2005-07-09
Hi there, new Ubuntu-user here signing in. I have installed Hoary on a Thinkpad A31 and I love it so far. I have two questions though.

1. I need the Java plugin for Firefox. I've tried installing it from Synaptic (Advanced>marked Java common) and several variations of sudo apt-get install *filename* but without success. What am I doing wrong?

2. I can't install the ClearLooks theme (or any other theme for that matter). I've tried Themes>Install theme>path to the ClearLooks index.theme-file but all I get is an error message that says "Invalid file format" or something like that. 

Any help would be appreciated.

---

### Post by parktownprawn on 2005-07-09
You may have to [enable additional repositories](http://ubuntuguide.org/#extrarepositories) 

1. to install java  plugin for firefox try the [ubuntu guide](http://ubuntuguide.org/#jre)  or the [wiki](http://wiki.ubuntu.com/Java) 

2. to install clearlooks try ```
sudo apt-get install gtk2-engines-clearlooks
``` 

by the way 
```
apt-cache search 
``` is quite usefull

for example ```
apt-cache search clearlooks
``` 

gives

```
gtk2-engines-clearlooks - ClearLooks theme
```

---

