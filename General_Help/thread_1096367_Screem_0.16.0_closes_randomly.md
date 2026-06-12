---
title: "Screem 0.16.0 closes randomly"
date: 2009-03-14
forum: General Help
---

### Post by happinesskills on 2009-03-14
yeah. Screem HTML/XML Editor version 0.16.0 randomly closes on me.

Also, I found that 0.17.1 has come out, but that was in January 2006, so I'm assuming development has died.

---

### Post by kellemes on 2009-03-14
> **happinesskills said:**
> yeah. Screem HTML/XML Editor version 0.16.0 randomly closes on me.

Also, I found that 0.17.1 has come out, but that was in January 2006, so I'm assuming development has died.

Indeed.. [http://en.wikipedia.org/wiki/SCREEM]("http://en.wikipedia.org/wiki/SCREEM")

---

### Post by happinesskills on 2009-03-14
sad.



but it still closes randomly

PS: I'm on Intrepid

---

### Post by kellemes on 2009-03-14
> **happinesskills said:**
> sad.



but it still closes randomly

PS: I'm on Intrepid

Run it from terminal and see if there is some output when the app crashes.

---

### Post by happinesskills on 2009-03-14
here's what come out.

```
me@my-computer:~$ screem

(screem:23564): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(screem:23564): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(screem:23564): Gtk-WARNING **: Refusing to add non-unique action 'cancel drag' to action group 'ScreemActions'

(screem:23564): screem-CRITICAL **: screem_page_is_feature: assertion `SCREEM_IS_PAGE( page )' failed

(screem:23564): screem-CRITICAL **: screem_page_is_xml: assertion `SCREEM_IS_PAGE( page )' failed

(screem:23564): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
^C
me@my-computer:~$ 
```

It closed while I was typing "monospace" into my CSS file

---

### Post by kellemes on 2009-03-14
Can't help you here, I guess Screem does depend on a hole lot of libraries of version "very old".
I'd look for alteratives..

---

### Post by happinesskills on 2009-03-14
I ran it again & it stayed open for a _whole minute!_ but once again, closed. here's the output:

```
me@my-computer:~$ screem

(screem:23720): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(screem:23720): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(screem:23720): Gtk-WARNING **: Refusing to add non-unique action 'cancel drag' to action group 'ScreemActions'

(screem:23720): screem-CRITICAL **: screem_page_is_feature: assertion `SCREEM_IS_PAGE( page )' failed

(screem:23720): screem-CRITICAL **: screem_page_is_xml: assertion `SCREEM_IS_PAGE( page )' failed

(screem:23720): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 10:1:could not recognize next production
parsing error: 17:1:could not recognize next production
parsing error: 19:1:while parsing ruleset: next construction should be a declaration
parsing error: 17:1:could not recognize next production
parsing error: 19:1:while parsing ruleset: next construction should be a declaration
parsing error: 17:1:could not recognize next production
Terminated
me@my-computer:~$ 
```


also, the "Terminated" at the end is where I ended it's process through the System Monitor because for some reason it stays open in the processes.

---

### Post by zmartant on 2009-10-24
I too suffer from the same issue.  Does anyone know of a comparable application?  I have tried Blufish Editor, not as nearly as nice as Screem in auto completion.  Should someone out there know of a comparable app, please post!

Thanks!

---

