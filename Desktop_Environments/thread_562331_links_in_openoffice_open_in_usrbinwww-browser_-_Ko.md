---
title: "links in openoffice open in /usr/bin/www-browser - Konsole"
date: 2007-09-28
forum: Desktop Environments
---

### Post by barthng on 2007-09-28
I  have run into a problem for which I can not find a solution.
I tried to get Kubuntu to open urls in Firefox instead of in Konqueror. First I had to add Firefox to the alternatives (It was not listed there). I have done this by update-alternatives --install firefox x-www.browser /usr/bin/firefox and idem /usr/lib/firefox/firefox and idem /usr/lib/firefox/firefox-bin. Then the misbehaviour started. All links clicked in OpenOffice open in /usr/bin/www-browser - Konsole; that is in a terminal.

I tried to undo everything with the --remove command. However I have not been able to return to the status quo ante. What I get now when clicking an url in openoffice is that the url opens in a terminal: /usr/bin/www-browser - Konsole.

Who can help me to get things right again and preferably also to get Firefox as the default browser from any application

Bart

---

### Post by llamakc on 2007-09-28
Let's see the output of 

```

update-alternatives --list x-www-browser

```and then where THOSE symlinks actually point to, so something like this would do it just fine:

```

for i in `update-alternatives --list x-www-browser`; do ls -lh $i; done

```Actually this would help explain anything you may have changed:

```

update-alternatives --list x-www-browser | xargs ls -lh

```Let's see the results of that last one, please.

COOL. update-alternatives has a command to help out too.

```

update-alternatives --display x-www-browser

```

Neat.

---

### Post by barthng on 2007-09-29
Thanks,

The outcomes of the tests are as follows:

/usr/lib/firefox/firefox-bin
/usr/bin/konqueror

-rwxr-xr-x 1 root root 11M 2007-07-26 04:11 /usr/lib/firefox/firefox-bin
-rwxr-xr-x 1 root root 3.0K 2007-09-25 19:38 /usr/bin/konqueror

-rwxr-xr-x 1 root root 3.0K 2007-09-25 19:38 /usr/bin/konqueror
-rwxr-xr-x 1 root root  11M 2007-07-26 04:11 /usr/lib/firefox/firefox-bin

x-www-browser - status is manual.
 link currently points to /usr/bin/konqueror
/usr/lib/firefox/firefox-bin - priority 1000
/usr/bin/konqueror - priority 80
Current `best' version is /usr/lib/firefox/firefox-bin.

Bart

---

### Post by llamakc on 2007-09-29
update-alternatives --auto x-www-browser

update-alternatives --config x-www-browser

(and choose the one you want).

---

### Post by barthng on 2007-09-30
Thanks again; I did update-alternatives --auto x-www-browser
and update-alternatives --config x-www-browser.
The result however is disappointing, I still get the link from openoffice opened in a terminal instead of in the browser.
When I click a link from Thunderbird, it duly opens in Firefox (I aranged for Firefox to be the default in the config file).
Could it be that this has something to do with an elusive OpenOffice setting? I spitted around but could not find anything. In other text editors as Kwrite or Kate I did not find how to get a working hyperlink so I failed to test this from another program.

Bart

---

### Post by llamakc on 2007-09-30
[http://www.oooforum.org/forum/viewtopic.phtml?t=55923&highlight=hyperlinks+open+terminal](http://www.oooforum.org/forum/viewtopic.phtml?t=55923&highlight=hyperlinks+open+terminal)

Have you seen that thread? IS there a setting in KDE's config dialogs that dictates what to open links with?

---

### Post by barthng on 2007-10-01
This confirms that it is an Oo issue.
Indeed an url on the desktop duly opens in Firefox.
I have not yet succeeded in solving the Oo issue though.
Editing the openurl file is beyond me; I will ask my son who is an accomplished programmer to look into this.

B.

---

### Post by llamakc on 2007-10-01
Tell him to look at this file:

/usr/lib/openoffice/program/open-url

---

### Post by Buddha443556 on 2008-01-12
I was having trouble openning hyperlinks in Firefox from OpenOffice documents too. I added a symlink "x-www-browser-bin" to /opt/firefox/ that pointed to /opt/firefox/firefox-bin that seems to have solved this problem.

---

