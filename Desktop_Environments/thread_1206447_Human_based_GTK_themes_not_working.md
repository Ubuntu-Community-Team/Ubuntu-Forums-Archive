---
title: "Human based GTK themes not working"
date: 2009-07-07
forum: Desktop Environments
---

### Post by bigboss0101 on 2009-07-07
Hi,

Using Ubuntu 8.04..2 on Sony Vaio notebook. 

None of the Human based GTK themes (like Human Redux, Human Reprise, Ljuda Human)  is working for me. They are getting applied but it looks ugly, odd and broken. Several other themes are working great. I have installed all gtk themes engines and also nodoka theme engine. But other Human themes that come built-in with Ubuntu (Human-clearlooks, Human-murrine etc) are working fine. What could be the prob?
I have attached screenshots of both faulty theme and actual theme.

---

### Post by bigboss0101 on 2009-07-07
Share your experience n knowledge and help out pls :)

---

### Post by Fzang on 2009-07-07
Maybe you're having issues or missing the engine that Human requires. I'm not sure but I think it uses the murrine engine. Try install/reinstall and see what happens.

---

### Post by bigboss0101 on 2009-07-09
Well I upgraded from Hardy to Intrepid and then to Jaunty and themes are working fine in Jaunty. Hope this info helps someone.

---

### Post by Vaun on 2009-07-09
Could you please?

```
sudo apt-get install thewidgetfactory
```

Commandline:

```
twf
```

And post a screen shot using Redux of the widget factory?

I got aggravated and deleted the them from Ubuntu-Art.org.

I'm trying to troubleshoot the issues for new users.

---

### Post by bigboss0101 on 2009-07-09
Redux is still not working for me. Seems like there is a bug in the package I downloaded (and may be you too). I installed and started twf and selected Redux and it throwed the following error in the terminal.

```
/usr/share/themes/Human-Redux/gtk-2.0/gtkrc:297: error: unexpected identifier `style', expected character `}'

```Following Human based themes are working fine. I have attached screenshots of all themes (except Human-ME bcoz max attachments is 5).

Human-netbook-murine
Human-Reprise
Ljuda-Human
Human-nature
Human-ME (Muslim Edition)

---

### Post by bigboss0101 on 2009-07-09
I just got in touch with Redux creator (his email in gtkrc file) and he said that he is working on a fix.

---

### Post by 6205 on 2009-07-10
Maybe you're missing some GTK engines like Murrine or GTK engine pixbuf..

---

### Post by bigboss0101 on 2009-07-10
No, all required engines are installed. There was some bug in the package itself. User Vaun himself is the creator of the Human-Redux theme. And he is working on it now.

---

### Post by Vaun on 2009-07-10
bigboss,


Please try to rebuild gtk-nodoka-engine.  The theme is perfect itself.  I'll attach the most recent version from trunk.  Make sure you have the developer tools installed.

Screenshot of the most recent version attached.

```
git clone git://git.fedorahosted.org/nodoka
```

```
cd nodoka/gtk-nodoka-engine
mkdir m4
autoreconf -isvf
./configure --prefix=/usr --enable-animation
make 
```

```
sudo make install 
```

---

### Post by bigboss0101 on 2009-07-11
Its working fine now.

---

