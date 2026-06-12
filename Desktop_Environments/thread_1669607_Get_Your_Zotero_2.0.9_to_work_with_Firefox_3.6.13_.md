---
title: "Get Your Zotero 2.0.9 to work with Firefox 3.6.13 &amp; OpenOffice 3.2.1"
date: 2011-01-18
forum: Desktop Environments
---

### Post by Maximus_ARNP on 2011-01-18
I was having some (whole screen-full of pop-up) errors while I used Zotero's Firefox plugin to insert citations and bibliography in my research paper. Here is the solution:

Java version

To fix this error, you may need to switch Java versions. The Zotero plugin for OpenOffice requires the original Java by Sun (sun-java6) to be installed and selected as the default plugin.

In Ubuntu Linux, since version 10.04, that Java is in the “partner” repository, so first you need to add the partner repository:

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

(You can also do that using the “software sources” under System&#8594;Administration.)

Next, update your package information and install sun-java:

sudo apt-get update
sudo apt-get install sun-java6-plugin sun-java6-jre

(Once again you can do the same using System–>Administration–>Synaptics Package Manager.)

Finally, you need to set sun-java as the default plugin:

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/

Reference:
[http://www.zotero.org/support/word_processor_plugin_troubleshooting#component_loading_error1]("http://www.zotero.org/support/word_processor_plugin_troubleshooting#component_loading_error1")

---

