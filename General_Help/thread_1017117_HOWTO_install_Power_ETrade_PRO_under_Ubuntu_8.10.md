---
title: "HOWTO install Power ETrade PRO under Ubuntu 8.10"
date: 2008-12-20
forum: General Help
---

### Post by Adrian Nania on 2008-12-20
# to install Power ETrade PRO under Ubuntu 8.10
sudo apt-get remove -y sun-java6-fonts sun-java6-jre sun-java6-plugin sun-java6-bin &&
sudo apt-get install -y sun-java5-fonts sun-java5-jre sun-java5-plugin sun-java5-bin
# log-on to eTrade -> Trading & Portofolios -> Active Trading -> Power E*TRADE Pro -> LAUNCH
#       Open with: Sun Java 5.0 Web Start (default)
sudo apt-get remove -y sun-java5-fonts sun-java5-jre sun-java5-plugin sun-java5-bin &&
sudo apt-get install -y sun-java6-fonts sun-java6-jre sun-java6-plugin sun-java6-bin
# log-on to eTrade -> Trading & Portofolios -> Active Trading -> Power E*TRADE Pro -> LAUNCH
#       Open with: Sun Java 6.0 Web Start (default)
#       [X] Do this automatically for files like this from now on -> OK
# you will get a message:
#       Please wait while your stored java will be converted to version 6
# now Power E*TRADE Pro is up and running on Java 6
# Load your favorite layout from the directory where you saved it

---

