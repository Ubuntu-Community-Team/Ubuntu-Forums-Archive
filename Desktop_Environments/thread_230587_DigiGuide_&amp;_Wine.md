---
title: "DigiGuide &amp; Wine"
date: 2006-08-06
forum: Desktop Environments
---

### Post by FooAtari on 2006-08-06
Trying to run a windows application DigiGuide under Wine

When I try and run from terminal I get this...

allie@desktop:~$ wine "C:\Program Files\DigiGuide TV Guide\Client.exe"
wine: cannot find 'C:\Program Files\DigiGuide TV Guide\Client.exe'

Tried it this way to:

allie@desktop:~$ wine "C:\Program Files\DigiGuide TV Guide\Client.exe"
wine: cannot find 'C:\Program Files\DigiGuide TV Guide\Client.exe'


Why cant it find it? I have entered the correct path

---

### Post by Ramses de Norre on 2006-08-06
Does ```
wine "C:\Program Files\DigiGuide TV Guide\"Client.exe
``` work? Wine often acts strange here with paths.

---

### Post by FooAtari on 2006-08-06
Thanks, but no :(

*Details: Text ended before matching quote was found for ". (The text was 'wine "C:\Program Files\DigiGuide TV Guide\"Client.exe ')*

---

### Post by FooAtari on 2006-08-06
It seems to work with this command I think

wine "/media/hda1/Program Files/DigiGuide TV Guide/Client.exe"

But it takes around 5 mins to start, cannot connect to the internet and gets write errors...

---

