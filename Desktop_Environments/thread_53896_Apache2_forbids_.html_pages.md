---
title: "Apache2 forbids .html pages"
date: 2005-08-02
forum: Desktop Environments
---

### Post by qwert231 on 2005-08-02
I installed Apache2 through Synaptic. When I do [http://localhost](http://localhost) I get a file listing, and the only thing in there is the folder apache2-default. So I create a basic .html page. (It's well formed.) I refresh the [http://localhost](http://localhost) and get:
Forbidden

You don't have permission to access /index.html on this server.

What's the deal?

---

### Post by chiappa on 2005-08-03
hi qwert231,

what about the fileprmissions?

has the apache user (common: www-data) read accress on the index.html file?
is there a script alias or virual server configured in the httpd.conf?

---

