---
title: "Wubi install leads to update problems"
date: 2008-12-08
forum: General Help
---

### Post by megamindstorm101 on 2008-12-08
I installed ubuntu with wubi and then when I tried to install updates it worked great but I had to leave and I had to turn the computer off so I canceled to come back later.  When I came back it gave an error and told me to run...manually. So I went to run it and it said i needed passowrd but when i typed that password it says it didnt work. Im going to reinstall it but is there a way around this?

---

### Post by razvanescu on 2008-12-08
To run update manually, open a terminal window(Applications > Accessories > Terminal) and type in those two commands:

sudo apt-get update
sudo apt-get upgrade

The first command updates the APT database and the second one upgrades all installed packages on your system to the newest version. This may result in a lot of downloads, but everything goes automatically.

---

