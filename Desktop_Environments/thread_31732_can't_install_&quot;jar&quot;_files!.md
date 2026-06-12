---
title: "can't install &quot;jar&quot; files!"
date: 2005-05-04
forum: Desktop Environments
---

### Post by lorap on 2005-05-04
i've java-common package installed but when i try to install say this:
sudo java -jar /tmp/red_cats.jar
i get an error:
sudo: java: command not found
what should i do?
thanx
pavel

---

### Post by shakin on 2005-05-04
[QUOTE=lorap]i've java-common package installed but when i try to install say this:
sudo java -jar /tmp/red_cats.jar
i get an error:
sudo: java: command not found
what should i do?
thanx
pavel[/QUOTE]

```

$ locate java

```

Is Java installed properly? It's obviously not in your path.

Here's how to install it: [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by lorap on 2005-05-04
sudo i get this:
locate java
/var/lib/dpkg/info/java-common.postinst
/var/lib/dpkg/info/java-common.list
/var/lib/dpkg/info/java-common.prerm
/var/lib/dpkg/info/java-common.md5sums
/var/lib/doc-base/info/java-policy.list
/var/lib/doc-base/info/java-policy.status
/var/lib/doc-base/info/debian-java-faq.list
/var/lib/doc-base/info/debian-java-faq.status
/usr/share/doc/python2.4-xml/examples/test/output/test_javadom
/usr/share/doc/python2.4-xml/examples/test/test_javadom.py.gz
/usr/share/doc/java-common
/usr/share/doc/java-common/debian-java-policy
/usr/share/doc/java-common/debian-java-policy/.dhelp
/usr/share/doc/java-common/debian-java-policy/index.html
/usr/share/doc/java-common/debian-java-policy/c28.html
/usr/share/doc/java-common/debian-java-policy/c36.html
/usr/share/doc/java-common/debian-java-policy/x73.html
/usr/share/doc/java-common/debian-java-policy/x86.html
/usr/share/doc/java-common/debian-java-policy/x105.html
/usr/share/doc/java-common/debian-java-policy/x138.html
/usr/share/doc/java-common/debian-java-policy/c149.html
/usr/share/doc/java-common/debian-java-policy/c173.html
/usr/share/doc/java-common/README.Debian
/usr/share/doc/java-common/copyright
/usr/share/doc/java-common/policy.ps.gz
/usr/share/doc/java-common/changelog.gz
/usr/share/doc/java-common/debian-java-faq
/usr/share/doc/java-common/debian-java-faq/footnotes.html
/usr/share/doc/java-common/debian-java-faq/apA.html
/usr/share/doc/java-common/debian-java-faq/ch1.html
/usr/share/doc/java-common/debian-java-faq/ch10.html
/usr/share/doc/java-common/debian-java-faq/ch11.html
/usr/share/doc/java-common/debian-java-faq/ch2.html
/usr/share/doc/java-common/debian-java-faq/ch3.html
/usr/share/doc/java-common/debian-java-faq/ch4.html
/usr/share/doc/java-common/debian-java-faq/ch5.html
/usr/share/doc/java-common/debian-java-faq/ch6.html
/usr/share/doc/java-common/debian-java-faq/ch7.html
/usr/share/doc/java-common/debian-java-faq/ch8.html
/usr/share/doc/java-common/debian-java-faq/ch9.html
/usr/share/doc/java-common/debian-java-faq/.dhelp
/usr/share/doc/java-common/debian-java-faq/index.html
/usr/share/doc/java-common/dummy-packages
/usr/share/doc/java-common/dummy-packages/README
/usr/share/doc/java-common/dummy-packages/java-virtual-machine-dummy.control
/usr/share/doc/java-common/dummy-packages/java-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java1-runtime-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-runtime-dummy.control
/usr/share/doc/java-common/examples
/usr/share/doc/java-common/examples/classpath-from-jars-1
/usr/share/doc/java-common/policy.txt.gz
/usr/share/doc/java-common/policy.xml.gz
/usr/share/doc/java-common/html
/usr/share/doc-base/java-policy
/usr/share/doc-base/debian-java-faq
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-text-x-java.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-java-byte-code.png
/usr/share/vim/vim63/ftplugin/java.vim
/usr/share/vim/vim63/syntax/java.vim
/usr/share/vim/vim63/syntax/javacc.vim
/usr/share/vim/vim63/syntax/javascript.vim
/usr/share/vim/vim63/indent/java.vim
/usr/share/vim/vim63/compiler/javac.vim
/usr/share/mime/application/x-java.xml
/usr/share/mime/application/x-java-jnlp-file.xml
/usr/share/mime/application/x-javascript.xml
/usr/share/mime/text/x-java.xml
/usr/share/mime/text/x-javascript.xml
/usr/share/omf/java-policy
/usr/share/omf/java-policy/java-policy-C.omf
/usr/share/omf/debian-java-faq
/usr/share/omf/debian-java-faq/debian-java-faq-C.omf
/usr/share/gtksourceview-1.0/language-specs/java.lang
/usr/share/gtksourceview-1.0/language-specs/javascript.lang
/usr/share/gimp/2.0/patterns/java.pat
/usr/share/dia/xslt/dia-uml2java.xsl
/usr/share/automake-1.4/java-clean.am
/usr/share/automake-1.4/java.am
/usr/share/screem/tagtrees/javascript.tagtree
/usr/share/java
/usr/lib/python2.4/site-packages/twisted/internet/javareactor.py
/usr/lib/python2.4/site-packages/twisted/internet/serialport/javaserialport.py
/usr/lib/python2.4/site-packages/twisted/internet/serialport/javaserialport.pyo
/usr/lib/python2.4/site-packages/twisted/internet/serialport/javaserialport.pyc
/usr/lib/python2.4/site-packages/twisted/internet/javareactor.pyo
/usr/lib/python2.4/site-packages/twisted/internet/javareactor.pyc
/usr/lib/python2.4/site-packages/_xmlplus/dom/javadom.py
/usr/lib/python2.4/site-packages/_xmlplus/dom/javadom.pyo
/usr/lib/python2.4/site-packages/_xmlplus/dom/javadom.pyc
/usr/lib/python2.4/site-packages/_xmlplus/sax/drivers2/drv_javasax.py
/usr/lib/python2.4/site-packages/_xmlplus/sax/drivers2/drv_javasax.pyo
/usr/lib/python2.4/site-packages/_xmlplus/sax/drivers2/drv_javasax.pyc
/usr/lib/rpm/javadeps
/usr/lib/openoffice/sdk/linux/bin/javamaker
/usr/lib/site-python/epydoc/markup/javadoc.py
/usr/lib/site-python/epydoc/markup/javadoc.pyc
/usr/lib/site-python/epydoc/markup/javadoc.pyo

---

### Post by shakin on 2005-05-04
Yeah it looks like you need to follow The Guide's instructions to get it properly setup.

On a side note, is anybody else in favor of changing the unofficial guide's name to The Hitchhiker's Guide to Ubuntu?

---

### Post by lorap on 2005-05-04
thanks friend!
it did install java, now i'll check it in the work...

---

### Post by lorap on 2005-05-04
nope it still doesn't work...
when i try to do this:
java -jar file.jar
i get an error file.jar is wrong...
but i get this with any other file also...

---

### Post by shakin on 2005-05-04
Can you post the exact error message?

---

