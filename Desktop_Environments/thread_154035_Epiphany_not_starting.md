---
title: "Epiphany not starting"
date: 2006-04-02
forum: Desktop Environments
---

### Post by Veracon on 2006-04-02
Today I installed the Epiphany browser (using apt, since I don't need the latest version), and it appeared to work fine. However, I'm unable to start it. When I simply run (Alt+F2) 'epiphany', there's no trace whatsoever of it starting. When I try to run it using the gnome panel, it saying 'Starting Epiphany...' in the taskbar, but the browser never comes up.

What may be wrong?

---

### Post by hollywoodb on 2006-04-02
try running epiphany from a terminal to see what error it gives, if any.  I'm also curious to know why you would prefer epiphany over firefox ;)

---

### Post by Veracon on 2006-04-04
[QUOTE=hollywoodb]try running epiphany from a terminal to see what error it gives, if any.  I'm also curious to know why you would prefer epiphany over firefox ;)[/QUOTE]
It gives me this:
epiphany: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory

I copied libgtkembedmoz.so to /usr/lib/mozilla-firefox, and now I get this instead:
epiphany: symbol lookup error: /usr/lib/mozilla-firefox/libgtkembedmoz.so: undefined symbol: _ZTV24nsGetServiceByContractID

The reason I'm trying Epiphany is that Firefox doesn't run native (uses XUL, which is not *perfectly* translated) and  Epiphany appears to run much faster in BeatrIX.

---

### Post by hollywoodb on 2006-04-04
you copied libgtkembedmoz.so ***to*** /usr/lib/mozilla-firefox ....

/usr/lib/mozilla-firefox/libgtkembedmoz.so is provided by the 'firefox' package. (default Breezy firefox version 1.0.7)

perhaps you should check your firefox installation.  if you don't have firefox installed, install it. if epiphany works after that then file a bug that epiphany should depend on firefox.

---

