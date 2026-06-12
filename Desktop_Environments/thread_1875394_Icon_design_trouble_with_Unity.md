---
title: "Icon design trouble with Unity"
date: 2011-11-04
forum: Desktop Environments
---

### Post by Merenguey on 2011-11-04
Hello there,


Since I tried to install my printer and scanner, my desktop & folders icons are poor designed. Before, Unity worked perfectly. I imagine it is a matter with theme or something, but I can't get what I have to do.



Here a picture of the disaster : [[IMG]http://data.imagup.com/11/1135087823.png[/IMG]]("http://www.imagup.com/data/1135087824.html")


I do not know if it can help but here the procedure used to install my MP495 canon :

> mkdir ~/print; cd ~/canon
wget [http://files.canon-europe.com/files/soft40251/software/mp250%20printer%20dirver%203.40.tar](http://files.canon-europe.com/files/soft40251/software/mp250%20printer%20dirver%203.40.tar)
tar xvf ./mp250\ printer\ dirver\ 3.40.tar
tar zxvf ./cnijfilter-mp250series-3.40-1-deb.tar.gz; cd cnijfilter-mp250series-3.40-1-deb/packages
clear
uname -m

If the output is - i686 run:
sudo dpkg -i ./cnijfilter-common_3.40-1_i386.deb; sudo dpkg -i ./cnijfilter-mp250series_3.40-1_i386.deb; sudo apt-get -f install

If the output is - amd64 run:
sudo dpkg -i ./cnijfilter-common_3.40-1_amd64.deb; sudo dpkg -i ./cnijfilter-mp250series_3.40-1_amd64.deb; sudo apt-get -f install

Then run:
rm -r ~/print; mkdir ~/scan
cd scan
wget [http://files.canon-europe.com/files/soft40252/software/mp250%20scanner%20driver%201.60.tar](http://files.canon-europe.com/files/soft40252/software/mp250%20scanner%20driver%201.60.tar)
tar xvf ./mp250\ scanner\ driver\ 1.60.tar
tar zxvf ./scangearmp-mp250series-1.60-1-deb.tar.gz
cd scangearmp-mp250series-1.60-1-deb/packages
clear
uname -m

If the output is - i686 run:
sudo dpkg -i ./scangearmp-common_1.60-1_i386.deb; sudo dpkg -i ./scangearmp-mp250series_1.60-1_i386.deb; sudo apt-get -f install

If the output is - amd64 run:
sudo dpkg -i ./scangearmp-common_1.60-1_amd64.deb; sudo dpkg -i ./scangearmp-mp250series_1.60-1_amd64.deb; sudo apt-get -f install

Reboot and it should workAny of you get and idea to put back in order?


Thanks. I've tried my best to write a correct english (hard task for a frenchy ^^)

Merenguey

---

