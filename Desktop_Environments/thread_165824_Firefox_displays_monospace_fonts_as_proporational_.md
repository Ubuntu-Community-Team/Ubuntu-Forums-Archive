---
title: "Firefox displays monospace fonts as proporational in in some websites"
date: 2006-04-25
forum: Desktop Environments
---

### Post by fheinsen on 2006-04-25
On both Breezy and Dapper, Firefox incorrectly displays certain fonts as proportional instead of monospace. For example, see:

[http://biz.yahoo.com/prnews/060425/latu037.html]("http://biz.yahoo.com/prnews/060425/latu037.html")

Here are screenshots in Breezy and Dapper:
[ATTACH]8740[/ATTACH]  [ATTACH]8783[/ATTACH]

This can be fixed by ediing the fonts.conf file, but should work out of-the-box, so I've filed a Launchpad bug report:
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/41294]("https://launchpad.net/distros/ubuntu/+source/firefox/+bug/41294")

---

### Post by fheinsen on 2006-04-30
Copying and pasting this into the /etc/fonts/local.conf file solves this problem:


 *** COPY OF /etc/fonts/local.conf ***
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
  <fontconfig>
  <!--
  Replace family "courier" with 'monospace'
-->
        <match target="pattern">
                <test qual="any" name="family">
                        <string>courier</string>
                </test>
                <edit name="family" mode="assign">
                        <string>Courier New</string>
                </edit>
        </match>
  </fontconfig>

 
***

---

