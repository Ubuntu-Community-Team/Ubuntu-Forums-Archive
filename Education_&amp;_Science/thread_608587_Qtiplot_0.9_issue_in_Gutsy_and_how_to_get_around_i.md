---
title: "Qtiplot 0.9 issue in Gutsy and how to get around it"
date: 2007-11-10
forum: Education &amp; Science
---

### Post by der_vegi on 2007-11-10
Qtiplot ([http://soft.proindependent.com/qtiplot.html]("http://soft.proindependent.com/qtiplot.html")) is a very good alternative to Origin, you can easily manipulate and plot data, do curve fitting and stuff like that.
Since Gutsy, version 0.9-rc1 is in the repos but does not work properly (at least on amd64): It crashes, if you minimize a plot window, for example. The developer told me, that this is an issue of the Qt-version, Qt 4.3 is not fully backwards compatible to Qt 4.2 but Qtiplot 0.9 is done for Qt 4.2, version 0,9.2 will start using Qt 4.3.

So if you want to use Qtiplot 0.9 in Gutsy, you have to install the libqt4-versions from Feisty and use 'package' => 'freeze version' to prevent updating in synaptic. For me, this works fine now, I installed the following libs from Feisty:

libqt4-core, libqt4-gui, libqt4-qt3support, libqt4-sql, python-qt4, python-sip4

I would also recommend to use the binary from the webpage, as the release-candidate still has some issues. Also, the preview of version 0.9.1 looks very promising... :)

---

