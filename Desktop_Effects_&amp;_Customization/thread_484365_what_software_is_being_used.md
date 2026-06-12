---
title: "what software is being used?"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by don gino on 2007-06-25
What software is being used in this screenshot?

[http://ubuntuforums.org/g/index.php?n=717](http://ubuntuforums.org/g/index.php?n=717)

How do they get those effects?

Thanks

---

### Post by tgm4883 on 2007-06-25
Looks like a mac theme and a desklet program, like adesklets or gdesklets

---

### Post by andrewsomething on 2007-06-25
Those are Screenlets.

From their[website]("http://hendrik.kaju.pri.ee/screenlets/?q=node/5"):

> Add the following to your source list (sudo gedit /etc/apt/sources.list)

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

if you are using feisty.

Then run this in a terminal:

wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then you can install screenlets with 'sudo apt-get install screenlets'. The package also includes updated third-party screenlets and utilities (Control panel, tray-icon)

You need to be running Beryl or Compiz to make them work.

If not, look into gDesklets. They work without Beryl or Compiz. Just type "sudo apt-get gdesklets" in the terminal or search on Synaptic.

---

