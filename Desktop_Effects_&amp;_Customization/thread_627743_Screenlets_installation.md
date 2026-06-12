---
title: "Screenlets installation"
date: 2007-11-30
forum: Desktop Effects &amp; Customization
---

### Post by charge1 on 2007-11-30
I am using this website to install screenlets [http://screenlets.org/index.php/FAQ](http://screenlets.org/index.php/FAQ)

[B]Goto System-> Administration -> Synaptic Package Manager and open up Settings -> Repositories. In the tab 'Third-Party Software' press the 'Add' button. In the dialog window enter this line:

deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets[/B]

After I hit reload I get the below message:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7

What I need to do to fix that?

---

### Post by rundee_f on 2007-11-30
u should ignore that message and continue the next step getting the GPG file..

**wget [http://download.tuxfamily.org/screenlets/hendrikkaju.gpg](http://download.tuxfamily.org/screenlets/hendrikkaju.gpg) -O- | sudo apt-key add -**

continue the FAQ...

---

### Post by charge1 on 2007-12-01
Why the website don't work now? [http://www.screenlets.org/](http://www.screenlets.org/)

---

### Post by FuturePilot on 2007-12-01
> **charge1 said:**
> Why the website don't work now? [http://www.screenlets.org/](http://www.screenlets.org/)

Must be down. Not working here either

---

### Post by charge1 on 2007-12-01
I use this websites

[http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

[http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5)

And it look like every think working for now.

Thanks for now

---

