---
title: "Evolution: Can't import GPG certificates"
date: 2005-03-05
forum: Desktop Environments
---

### Post by pirast on 2005-03-05
Hi,
I just tried to import my GPG certificate into Evolution. But after I selected the location of the .asc file, entered the password for the "NSS User Private Key" into the field, clicked OK, entered the passwort for the "PKCS-12 File" into the field and clicked OK, there wasn't my certificate.

Then I started evolution via console.

Here the output:

> martin@mubuntu:~ $ evolution

(evolution:4951): camel-WARNING **: Invalid root: '/home/martin/.evolution/mail/local/Drafts.ibex.index'

(evolution:4951): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution:4951): camel-WARNING **: block size: 1024 (1024) OK

(evolution:4951): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution:4951): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution:4951): camel-WARNING **: flags: unSYNC

(evolution:4951): camel-WARNING **: Invalid root: '/home/martin/.evolution/mail/local/Outbox.ibex.index'

(evolution:4951): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution:4951): camel-WARNING **: block size: 1024 (1024) OK

(evolution:4951): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution:4951): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution:4951): camel-WARNING **: flags: unSYNC

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

** (evolution:4951): WARNING **: Invalid UTF8 string passed to pango_layout_set_text()

(evolution:4951): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 38: Element »markup« wurde geschlossen, aber das derzeit offene Element ist »b«

(evolution:4951): Gtk-CRITICAL **: file gtktreesortable.c: line 137 (gtk_tree_sortable_set_sort_column_id): assertion `GTK_IS_TREE_SORTABLE (sortable)' failed

importing pkcs12 from `/mnt/win6/Martin Juergens [email]martin@gamesplace.info[/email] (*) pub-sec.asc'
handle_error (7)
 

> handle_error (7) is the output when I click the last time on OK.

Could you please help me?

Greetings,
Martin

---

### Post by kassetra on 2005-03-05
Are you running Evolution 2.0.2 by any chance?

---

### Post by pirast on 2005-03-05
Hi,
Yes. I also installed the update (I think it was a security update) with apt-get.

Greetings,
Martin

---

### Post by kassetra on 2005-03-05
[QUOTE=pirast]Hi,
Yes. I also installed the update (I think it was a security update) with apt-get.

Greetings,
Martin[/QUOTE]

That's what I thought.  Ok, from what I know (and I'm going to keep poking around to find out more) Evolution 2.0.2 has a bug that's preventing you from importing that certificate.  I believe it's been fixed in 2.0.3, but let me see if I can find a fix for you.

---

### Post by pirast on 2005-03-05
[QUOTE=kassetra]That's what I thought.  Ok, from what I know (and I'm going to keep poking around to find out more) Evolution 2.0.2 has a bug that's preventing you from importing that certificate.  I believe it's been fixed in 2.0.3, but let me see if I can find a fix for you.[/QUOTE]
 That would be very nice. Thanks!

Do you know whether the bug will be fixed in the next ubuntu release?

---

### Post by kassetra on 2005-03-05
[QUOTE=pirast]That would be very nice. Thanks!

Do you know whether the bug will be fixed in the next ubuntu release?[/QUOTE]

I'm sure the next version of ubuntu will have the latest software, so I'm assuming that if they don't have it as soon as hoary is launched, it will be available very soon.  Still poking around a bit... I need to test something and see what it does before I tell you to try it (I'd hate to have you do something that causes problems!)

---

### Post by pirast on 2005-04-08
[QUOTE=kassetra]I'm sure the next version of ubuntu will have the latest software, so I'm assuming that if they don't have it as soon as hoary is launched, it will be available very soon.  Still poking around a bit... I need to test something and see what it does before I tell you to try it (I'd hate to have you do something that causes problems!)[/QUOTE]
 I just upgraded to hoary.

And there is the same error :-/

Any help?

Greetings,
Martin

---

