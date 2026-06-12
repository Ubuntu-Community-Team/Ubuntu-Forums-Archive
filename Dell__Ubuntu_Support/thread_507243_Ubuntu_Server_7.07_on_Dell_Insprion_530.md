---
title: "Ubuntu Server 7.07 on Dell Insprion 530??"
date: 2007-07-22
forum: Dell  Ubuntu Support
---

### Post by ittybitty9bees on 2007-07-22
Hi all,

I'm new to the linux community, so forgive my ignorance.  I just purchased a Dell 530n with ubuntu 7.03 desktop edition preloaded on it.  However, because of what I need to accomplish I want to load ubuntu 7.03 SERVER edition on it.  As i was attempting to do this through the installation cd i downloaded from ubuntu.com,  I encountered an error that it could not detect a network interface.  Any ideas?

Also I tried loading v. 6.6 LTS on it first, with no luck, as that apparently didn't have any drivers for my CDROM  (pbds dh-48c2s)

Has anybody successfully installed 7.04 Server Edition on the new Inspiron 530n's yet?

Thanks.

---

### Post by sciurus on 2007-07-22
Rather than install the server edition, why not install the server software you need on the desktop edition?

Launch System -> Help, then click "Adding, Removing and Updating Applications" for mor einformaiton on how to install software.

---

### Post by Ek0nomik on 2007-07-23
> **ittybitty9bees said:**
> Hi all,

I'm new to the linux community, so forgive my ignorance.  I just purchased a Dell 530n with ubuntu 7.03 desktop edition preloaded on it.  However, because of what I need to accomplish I want to load ubuntu 7.03 SERVER edition on it.  As i was attempting to do this through the installation cd i downloaded from ubuntu.com,  I encountered an error that it could not detect a network interface.  Any ideas?

Also I tried loading v. 6.6 LTS on it first, with no luck, as that apparently didn't have any drivers for my CDROM  (pbds dh-48c2s)

Has anybody successfully installed 7.04 Server Edition on the new Inspiron 530n's yet?

Thanks.

I just want to point out that the Ubuntu Desktop Edition is 7.04 as well.  :)

The only difference between the Desktop Edition and the Server Edition, is that the Server Edition doesn't have a Graphical Interface, and will come with an option to install the stack of server software (Apache/PHP/MySQL) during the installation.

You can run a server using the Desktop Edition, you will simply have a GUI alongside with it.

So, if you don't want a GUI, than you will want to install the Server Edition.  If you do want the GUI, you can still install the widely used server software without any hassle.

If you could post the exact error message you are getting, it would make it easier to find a solution for your Server Edition install.

---

### Post by ittybitty9bees on 2007-07-24
Well, I actually decided (for the time being) to just run servers on the desktop edition.  Right now this is acceptable only because my projects are new and generate no load on the server (web server, mail server and such) but at some point ( hopefully :D:D  )   the traffic and load being handled by my server will be high enough that I would need the precious memory and processor time that the GUI sits there and consumes (right now there's no monitor or mouse hooked up to my desktop, i do everything through SSH) hence the need for the server edition.  Maybe by then 7.04 will be updated and the issue will be closed.

Thanks everyone

---

### Post by rrmoulton on 2007-07-26
There's a bunch of us with 530's with invisible NICs.  This fix has been posted in a few other places.  Download the attached to your home directory.  Open terminal.

Code:
tar xfvz e1000-7.6.5.tar.gz
cd e1000-7.6.5/src
sudo make install
sudo modprobe e1000

OK, your Ubuntu will try to obtain an IP address automatically now. If not, you might want to edit /etc/network/interfaces to configure it manually,

(I did it in System / Administration / Network)

then run this command:

Code:
sudo /etc/init.d/network restart

If it still not work, reboot your Ubuntu.

My NIC came right up.

Let us know how it worked.

Good Luck.

---

