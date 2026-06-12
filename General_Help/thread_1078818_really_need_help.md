---
title: "really need help"
date: 2009-02-23
forum: General Help
---

### Post by portland1982 on 2009-02-23
I  just bought a computer that has ubuntu. I tried to  download my pokerstars and fulltilt account on here but it    wont open it it keeps asking me  what program to open  it with. Can someone please tell me how to finish downloading the program and open it up so i can play. i miss it so. thanks for the help

---

### Post by howefield on 2009-02-23
Those sites require you to install an .exe file, which can't be opened in Ubuntu without something like Wine.

I think you'd need to install Wine using Synaptic Package Manager, then right click on .exe file and select "open with wine installer"

---

### Post by portland1982 on 2009-02-23
where do i find the exe file int the synaptic package manager
?

---

### Post by howefield on 2009-02-23
Sorry if I wasn't clear, you first install Wine from Synaptic Package Manager, and then download the .exe file from your poker website, eg to your desktop, then right click your downloaded file and choose install with wine...

BTW, it is not guaranteed to work, Wine won't make every windows executable work. I am downloading pokerstars right now to try it.

---

### Post by mb_webguy on 2009-02-23
No, you're misunderstanding what he said.

You need to install Wine, which is a compatibility layer allowing you to run (many, but not all) Windows applications in Linux.  You can install it using Add/Remove Applications or Synaptic Package Manager (search for "wine"), but to get the latest version of Wine you need to add the [WineHQ repository]("http://www.winehq.org/download/deb") to your software sources first.  *Then* install Wine using Add/Remove Applications, Synaptic, or in the terminal using the command "sudo apt-get install wine".

Once you do that, you should be able to double-click on the exe file to install or run your Windows software.  As I said, not all Windows applications will run under Wine.  You can use the [Wine AppDB]("http://appdb.winehq.org/") website to check for compatibility.

---

### Post by howefield on 2009-02-23
ok, the good news is that it worked a treat. Might even start playing poker again ;-)

---

