---
title: "Alexandria 0.6.1 and Tellico 1.0"
date: 2005-11-10
forum: Closed Requests
---

### Post by montag on 2005-11-10
Alexandria is a GNOME application to help you manage your book collection.

0.6.1 is in Dapper:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alexandria&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alexandria&searchon=names&subword=1&version=dapper&release=all)

 Tellico is a KDE application for organizing your collections.
1.0 is in Dapper:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tellico&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tellico&searchon=names&subword=1&version=dapper&release=all)

N.B. Tellico 1.0 is not the last release (which is 1.0.3), but it's what Dapper offers... ;-) Maybe it's a good idea wait for 1.0.3 is in Dapper before backporting it? I don't know...

Thank you very much for this work...

---

### Post by jdong on 2005-11-11
Accepted -- Thanks!

---

### Post by jdong on 2005-11-12
Both look like they'll build fine -- Alexandria already went through, Tellico well underway.

---

### Post by graabein on 2005-11-23
Anyone know how to solve this error?

$ **alexandria**```

/usr/local/lib/site_ruby/1.8/alexandria/book_providers/z3950.rb:18:in `require': no such file to load -- zoom (LoadError)
        from /usr/local/lib/site_ruby/1.8/alexandria/book_providers/z3950.rb:18
        from /usr/local/lib/site_ruby/1.8/alexandria/book_providers.rb:238
        from /usr/local/lib/site_ruby/1.8/alexandria.rb:88
        from /usr/bin/alexandria:7
```
Maybe wipe the providers dir?


Edit: I found [http://blog.gmane.org/gmane.comp.gnome.apps.alexandria/]("http://blog.gmane.org/gmane.comp.gnome.apps.alexandria/")

---

### Post by graabein on 2005-11-25
I spoke with one of the developers:

> You need to install Ruby/ZOOM, a new dependency introduced in 0.6.0 for Z39.50 queries.

Ruby/ZOOM can be downloaded from there:

[http://ruby-zoom.rubyforge.org/](http://ruby-zoom.rubyforge.org/)

And it depends from the YAZ library (which is packaged in Debian/Ubuntu).

Note that the CVS version of Alexandria is now using this library as non-mandatory.  If the library is not found then Z39.50 support is not available.

---

### Post by felipefoz on 2006-06-25
i'm having problem when i try to edit the names, something with the utf8! it shows an ? instead of the right letter like ê é or ã! then when i try to change, the applications closes suddenly!
check it out! 

```
felipe@Ubuntu:~$ alexandria
/usr/lib/ruby/1.8/alexandria/book_providers.rb: line 253
   Pango-WARNING **:Invalid UTF-8 string passed to pango_layout_set_text()
/usr/lib/ruby/1.8/alexandria/book_providers.rb: line 253
   Pango-WARNING **:Invalid UTF-8 string passed to pango_layout_set_text()
/usr/lib/ruby/1.8/alexandria/book_providers.rb: line 253
/usr/lib/ruby/1.8/alexandria/ui/glade_base.rb: line 26
   Pango-WARNING **:Invalid UTF-8 string passed to pango_layout_set_text()
/usr/lib/ruby/1.8/alexandria/ui/glade_base.rb: line 26
   GLib-CRITICAL **:g_utf8_casefold: assertion `str != NULL' failed

```

---

### Post by charles woodward on 2006-06-26
my problem is quite simple - I had a listof books held under Abebooks Homebase - I imported this into tellico - no problems (although I may need to edit somethings)

According to Alexandria it can import tellico files (*.tc)  - so I tried to import the file into alexandria  - Mybooks.tc is `not a recognized format`.  Why not - alexandria only accepts imports from Tellico - and these have a tc suffix.  Well I have set up a file using Tellico, I can edit that file, and it has a .tc suffix.  Any ideas as to why Alexandria can't recognise it?

---

### Post by Ferio on 2007-02-17
I've just entered here to look information about this odd behaviour; I'm using Tellico under GNOME to manage my books and DVDs collections, and I wanted to switch to Alexandria and GCFilms to get rid of KDE apps, but since the first is not importing the .tc files, I can't do it. Any idea anyone?

---

### Post by Ferio on 2007-04-25
The same thing happens with Feisty versions; in fact Alexandria is still 0.6.1 (which seems to be the latest version), while Tellico is 1.2.7. Does anyone know if Alexandria is still in development?

---

