---
title: "Printer Connection Message Box Persists"
date: 2008-06-23
forum: Desktop Environments
---

### Post by fuzzydoc on 2008-06-23
Xubuntu-7.10 and -8.04. Xfce-4.4.1 and -4.4.2.

Ever since I moved the hard drive from an IBM ThinkPad 600E to the Toshiba Tecra 8000, there is a message box that displays in the upper left corner. It  says:

"Printer connected?
"Printer laser5_duplex may not be connected."

This is the default printer, and it's a network node (not directly connected to any workstation or server.) The printer is normally off.

While I can close the message box, it reappears in a few seconds. Both /etc/cups/printers.conf and the browser interface to CUPS keep resetting the printer status to 'processing' rather than 'idle.'

How do I keep this message box from reappearing continuously? It annoys my wife because it covers part of the panel and any application window.

I've asked this question on the xubuntu mail list, but received no response. I've also asked on the Xfce mail list, but the one response there was ineffective. No local ubuntu user has responded to a message on the local LUG mail list. I hope that someone here knows what's going on and can  direct me to a solution.

---

### Post by fuzzydoc on 2008-06-24
Fixed.

To summarize: the IPP address displayed for the "Local" printer is not the default address of the "Server." The former was correctly specified as a socket while the latter was incorrectly specified as localhost. As soon as I changed the Server address to the socket the message box stayed away.

---

