---
title: "wget help"
date: 2009-01-23
forum: General Help
---

### Post by Mithrilhall on 2009-01-23
I'm trying to download a file called 'forms'. It has no extension.

[http://site.com/forms/incrementing_numbers/random_numbers/forms](http://site.com/forms/incrementing_numbers/random_numbers/forms)

I've been trying this with wget but I'm not sure how to do it properly.


Any suggestions?

---

### Post by nothingspecial on 2009-01-23
Bad link

---

### Post by Mithrilhall on 2009-03-18
wget was unable to do what I needed...but this did the trick.


[http://www.langfeldt.net/w3mir/](http://www.langfeldt.net/w3mir/)

---

### Post by fieroboom on 2009-03-18
Call me biased, but IMHO, wget (or curl) will pwn any similar 3rd party app...
I would be especially cautious since the very first line of that app's page says:

"WARNING: A serious bug was discovered in w3mir 1.0.8 (it is probably present in some earlier versions too), which can cause removal of all your files, not just files in the mirror. To avoid this edit w3mir, search for 'sub rm_rf  (line 2259 in 1.0.8 ) and put the statement 'die;' on the line below. After it should read:

sub rm_rf {
  die;

Instead of files being removed w3mir will now abort if the bug is triggered."

If you had posted a real link, and given us a little more time & info, we could have helped you with getting wget to do what you want.
Just my .02.
:D
-Paul

---

### Post by sahabcse on 2009-03-18
Hi


The link seems to be not found. Use wget -c for continuous download.

---

### Post by ruel- on 2009-03-18
Do something like:

```
wget <LINK> -O <DESIRED-FILE-NAME-WITH-EXTENSION>
```

---

