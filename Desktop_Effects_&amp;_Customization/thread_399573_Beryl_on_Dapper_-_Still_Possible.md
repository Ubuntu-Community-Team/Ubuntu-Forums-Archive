---
title: "Beryl on Dapper - Still Possible?"
date: 2007-04-02
forum: Desktop Effects &amp; Customization
---

### Post by led_scorched on 2007-04-02
is it still possible to install Beryl on Dapper?  Everything i have read so far says its unsupported as of march 19, and now i cant find any of the files to install it.

Is there a good source of the dapper files around?  or is Edgy the only way to get it anymore?

---

### Post by johnc4510 on 2007-04-02
Here is the wiki page you need:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.06.x_.28Dapper_Drake_-_Long_Term_Support.29](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.06.x_.28Dapper_Drake_-_Long_Term_Support.29)

---

### Post by led_scorched on 2007-04-02
ok... i did all of this.  now for another dumb question - how do i get it up and going?

---

### Post by johnc4510 on 2007-04-02
Open a terminal:

Applications>Accessories>Terminal

Type:

beryl-manager

Here is a good posting to read through for other hints:

[http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

---

### Post by led_scorched on 2007-04-02
yielded this:
> bash: beryl-manager: command not found


---

### Post by led_scorched on 2007-04-02
tried the steps in the second link also, and it keeps hanging up on this:

[QUOTE=~$ sudo apt-get install beryl emerald-themes
]Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: beryl-manager but it is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages
[/QUOTE]

---

### Post by johnc4510 on 2007-04-02
Show me the link to the web page you are using to install beryl please.

---

### Post by led_scorched on 2007-04-02
[http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org)

---

### Post by johnc4510 on 2007-04-02
That looks to be the problem, those instructions are for edgy and fiesty. They won't work with dapper. Go to this page as listed above and see if those instructions work for dapper like it says.

[http://wiki.beryl-project.org/wiki/I...erm_Support.29](http://wiki.beryl-project.org/wiki/I...erm_Support.29)

---

### Post by led_scorched on 2007-04-02
that link you posted is empty

the link i posted is from the Ubuntuforum page you sent.

apperently neither is working :p

---

### Post by techstop on 2007-04-02
> **led_scorched said:**
> that link you posted is empty

the link i posted is from the Ubuntuforum page you sent.

apperently neither is working :p

The first link that johnc posted is correct, the second one is not a proper link. This is the correct link;

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.06.x_.28Dapper_Drake_-_Long_Term_Support.29](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.06.x_.28Dapper_Drake_-_Long_Term_Support.29)

Follow that, and then you'll find that you need to use an unofficial repo, see here;

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository)

---

### Post by FuturePilot on 2007-04-02
I don't know why the Ubuntu-beryl project repos have removed Dapper from them. That makes no sense. Dapper is supported until 2009. So you're going to have to use SVN repo if you want close to the latest version although I've found the SVN version a little buggy compared to the final version. I just don't understand why it seems that everyone is dropping support for Dapper:confused:

---

