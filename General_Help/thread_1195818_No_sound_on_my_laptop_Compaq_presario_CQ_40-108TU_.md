---
title: "No sound on my laptop Compaq presario CQ 40-108TU using Ubuntu 9.04"
date: 2009-06-24
forum: General Help
---

### Post by Amutha on 2009-06-24
No sound on my laptop Compaq presario CQ 40-108TU using Ubuntu 9.04. I am very new to Linux. Could anyone help?

---

### Post by ArihantBhudda on 2009-11-05
1. copy-paste the following command into the Terminal: 

gksudo gedit /etc/modprobe.d/alsa-base.conf 

2. and add these lines to the end of the /etc/modprobe.d/alsa-base.conf file: 

# Keep snd-pcsp from beeing loaded as first soundcard 
options snd-pcsp index=-2 
alias snd-card-0 snd-hda-intel 
alias sound-slot-0 snd-hda-intel 
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1 

3. Then navigate to System>Preferences>Sound and change everything to ALSA 

4. copy-paste the following command into the Terminal: 

gksudo gedit /etc/group 

5. replace the following line (or something very similar to it): 

audio: x:29 : pulse 

with this line: 

audio: x:29:joshua,pulse               

(delete the space before 'x' in above said line)
*[COLOR=Red][/COLOR]*6.Restart

I tried in my system it worked fine will work in your system also ...all the best..hope u will close this talk...

---

### Post by Amutha on 2010-04-07
Thanks. 9.10 fixes the issue.

---

