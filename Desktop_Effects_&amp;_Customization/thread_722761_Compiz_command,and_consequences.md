---
title: "Compiz command,and consequences"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by blackwash0 on 2008-03-12
I was trying to use the correct command in the terminal to get to the actual advanced compiz settings under the system tab. At first I typed

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O /tmp/freewins.zip [http://smspillaz.googlepages.com/freewins-0.3-0.6.zip](http://smspillaz.googlepages.com/freewins-0.3-0.6.zip)
mkdir -p  ~/compiz/ && cd ~/compiz
unzip /tmp/freewins.zip
cd ~/compiz/freewins-0.3-0.6
make clean
make
make install


per an online site. This is something I did by mistake. I've found out how to enable to the advanced compiz effects manager, but wanted to know, what does the above code mean? It unpacked a lot of files but the aborted, so was anything changed?  

Thanks for any help

---

### Post by scragar on 2008-03-12
if it aborted before(or close to the start of)```
make install
```then the odds are nothing was changed, and you can just delete your excess files/folders without worry, if make install did manage to install something then the odds are that it will not have any noticable effect(since you installed the compiz settings thing using synaptic odd's are any changes would have been undone anyway). All in all, odds of changes are very slim(under 5% I'd say), and the odd's of any changes that would have an effect will be even lower(say around 0.1%), so unless you start noticing some strange events I wouldn't worry.

---

### Post by blackwash0 on 2008-03-12
Thanks a lot! I feel so much better.

---

