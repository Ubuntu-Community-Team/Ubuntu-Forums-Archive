---
title: "Emblems in Nautilus"
date: 2012-09-03
forum: Desktop Environments
---

### Post by Philip Gray on 2012-09-03
Good evening

Please accept my apologies if this not the right place for this query. I am using Gnome Classic on 12.04.

In my efforts to get 12.04 to work like my 10.04 I have been searching the forums for ways in which to add the missing Emblem functionality in 12.04. Most of the suggestions that I have found on various forums work in 11.04/11.10 but not 12.04. I eventually downloaded and installed a python script which sort of works:- you can add icons but its' Clear option does not work.  So the only way to remove its' emblem is to delete the folder and then recreate it, which is rather tedious.

I then found that you needed to install the 'nautilus-actions-extra' package. I had a lot of issues doing this. To resolve them I had had to install libnautilus-extention1 and nautilus-gksu before synaptic would allow me to install the nautilus-actions-extra.

Well after all this effort I still do not have the Emblem functionality back. does anyone have any suggestions as to what I can do to get it?

Regards
Philip

---

### Post by Ravi5kumar on 2012-09-03
Hi,

Just type these commands in terminal:
```
sudo add-apt-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get install nautilus-emblemize

```After installing log out to see the changes. I am also running Ubuntu 12.04 with Gnome classic and its working fine. See the attachment.

---

### Post by Philip Gray on 2012-09-05
Hi Ravi5kumar

I was able to install the emblems and the 'set emblem' option is shown. However after I have attached them to a folder they do not show. A message is displayed advising that the folder has been updated. Do you perhaps know why this is occurring?

regards
Philip

---

### Post by Ravi5kumar on 2012-09-06
Try with default icon theme...

---

