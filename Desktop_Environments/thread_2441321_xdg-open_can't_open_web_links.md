---
title: "xdg-open can't open web links"
date: 2020-04-22
forum: Desktop Environments
---

### Post by Daniel_Rosehill on 2020-04-22
Hi folks,


I've been having this problem for the past year probably but it's now come to a head as it's preventing me from installing google-drive-ocamlfuse.


Whenever a CLI attempts to open a browser tab I get an error message and it appears as if my home directory is being automatically prefixed to the URL — so the command fails.


E.g. when I run google-drive-ocamlfuse in a terminal the program should open by default web browser (Chrome) and bring me to the login screen.


Instead I get:

```
[COLOR=#000000]*/home/myuser/https:/accounts.google.com/o/oauth2/auth?client_id=111111111111111.apps.googleusercont ent.com&redirect_uri=https%3A%2F%2Fgd-ocaml-auth.appspot.com%2Foauth2callback&scope=https%3A%2 F%2Fwww.googleapis.com%2Fauth%2Fdrive&response_typ e=code&access_type=offline&approval_prompt=force&s tate=454545454545454545454: No such file or directory*[/COLOR]

```

[https://i.imgur.com/wlT9fkR.png](https://i.imgur.com/wlT9fkR.png)

Does anybody know what might be causing this and what I need to change for CLIs to be able to open links again?

This is an LXDE specific bug - when I log out and use GNOME xde-open [www.url.com](www.url.com) works as expected and opens the link in my default browser (Chrome)

---

### Post by guiverc on 2020-04-22
> **Daniel_Rosehill said:**
> Hi folks,

I've been having this problem for the past year probably ...

This is an LXDE specific bug ...

You haven't specified a release (but I take it's 19.10 or 20.04 from ask.ubuntu), but please confirm.

The past year grabs me though; in April 2019 a $BROWSER issue was tasked to be addressed in Lubuntu and subsequently fixed (ie. LXQt), something specifically impacting chrome & chromium (maybe T53). The Lubuntu team no longer supports LXDE except in 18.04 so your release may matter (though my memory is vague as I'd have heard details only 3rd hand).

---

### Post by mc4man on 2020-04-22
See here for bug report and fix you can do
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=931822](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=931822)

upstream commit to fix
[https://gitlab.freedesktop.org/xdg/xdg-utils/commit/31525d3855f876ddf2e29091b2e8d376f923e09e](https://gitlab.freedesktop.org/xdg/xdg-utils/commit/31525d3855f876ddf2e29091b2e8d376f923e09e)

---

