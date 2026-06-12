---
title: "Cairo Dock Configuration menu Empty ,Pic attached"
date: 2012-10-29
forum: Desktop Environments
---

### Post by paichkash on 2012-10-29
hi
when i right click on cairo dock and click configure the menu pops up but its empty .. nothig is there in any tab.. when i click the Advanced butotn i do get a huge bucnch of complex and confusing things... :(

---

### Post by paichkash on 2012-11-03
bump time:guitar:

---

### Post by paichkash on 2012-11-09
no reply ?

---

### Post by slickymaster on 2012-11-09
It could be a permission problem, try to post at shell this command:
 
chmod u+rwx -R ~/.config/cairo-dock/

---

### Post by paichkash on 2012-11-10
> **slickymaster said:**
> It could be a permission problem, try to post at shell this command:
 
chmod u+rwx -R ~/.config/cairo-dock/


still the same ..
only when i click advanced settings i see those settings .. on basic all of the settings tabs are empty..

---

### Post by makitso on 2012-11-10
Might be your theme.  Same behavior with default one?

---

### Post by paichkash on 2012-11-10
> **makitso said:**
> Might be your theme.  Same behavior with default one?

didnt got ur question.. 

i installed the mac theme .. should i make a video and upload it to youtube ?

---

### Post by slickymaster on 2012-11-10
I have installed Greybird-Mac theme in Xubunto 12.10 and nothing went wrong with it.

Is this the one you installed? How did you installed it? It's just a simple drag and drop of the Greybird-Mac.tar.gz package to the styles list in settings manager > appearance.

---

### Post by paichkash on 2012-11-12
i installed Macbuntu-10.04 .. according to the method mentiond by it...
and this cairo dock was installed through synaptic..

---

### Post by slickymaster on 2012-11-12
Well, I have no idea how you've made your installation, but to install that theme you just have to post these commands in terminal:

wget [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.04/v2.0/Macbuntu-10.04.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.04/v2.0/Macbuntu-10.04.tar.gz) -O /tmp/Macbuntu-10.04.tar.gz
tar xzvf /tmp/Macbuntu-10.04.tar.gz -C /tmp
cd /tmp/Macbuntu-10.04/

$ ./install.sh

---

