---
title: "problems with java versions and gij -jar command"
date: 2005-11-22
forum: Desktop Environments
---

### Post by SilvioTO on 2005-11-22
Hi, I'm installed java following the ubuntuguide installed on my system but file .jar don't run. For example if I run JOGL -Install.jar for use ww2d it return the following error message:

WW2D JOGL installer 0.99.87 (1.1.1) by Vitaliy Pronkin <pronvit@gmail.com>
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.SwingUtilities.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.RepaintManager.addInvalidComponent(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.revalidate() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.setOpaque(boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel(java.awt.LayoutManager, boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.createGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.getGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.JRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.createRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.getRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.frameInit() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.JFrame() (/usr/lib/libgcj.so.6.0.0)
   at org.ww2d.jogl.InstForm.InstForm() (Unknown Source)
   at org.ww2d.jogl.Installer.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:JOGL-Inst.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more

If I'm install official java inrepositories "j2re-sun... version 1.4" the installer work and ww2d run ok.

Now I have installed only the latest java version using metod descripted on guide (from bin file using fakeroot), but when I type command java --version in terminal the output is 1.4.2 version... :???:, but on [www.java](www.java). com/verify version is the correct version 1.5.0_05. I don't understand.

Follow the log of installation of java. Contain some errors "permission denied".

extracting: jre1.5.0_05/lib/zi/Etc/GMT-7
  inflating: jre1.5.0_05/lib/zi/Etc/GMT+6
 extracting: jre1.5.0_05/lib/zi/Etc/GMT+11
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-14
  inflating: jre1.5.0_05/lib/zi/Etc/GMT+2
 extracting: jre1.5.0_05/lib/zi/Etc/GMT-5
 extracting: jre1.5.0_05/lib/zi/Etc/GMT-13
 extracting: jre1.5.0_05/lib/zi/Etc/GMT+3
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-4
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-12
  inflating: jre1.5.0_05/lib/zi/Etc/GMT+4
 extracting: jre1.5.0_05/lib/zi/Etc/GMT+9
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-1
 extracting: jre1.5.0_05/lib/zi/Etc/GMT+5
  inflating: jre1.5.0_05/lib/zi/Etc/GMT
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-2
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-6
 extracting: jre1.5.0_05/lib/zi/Etc/GMT-9
  inflating: jre1.5.0_05/lib/zi/Etc/GMT+10
  inflating: jre1.5.0_05/lib/zi/Etc/GMT-10
   creating: jre1.5.0_05/lib/zi/Europe/
  inflating: jre1.5.0_05/lib/zi/Europe/Chisinau
  inflating: jre1.5.0_05/lib/zi/Europe/Moscow
  inflating: jre1.5.0_05/lib/zi/Europe/Paris
  inflating: jre1.5.0_05/lib/zi/Europe/Riga
  inflating: jre1.5.0_05/lib/zi/Europe/Lisbon
  inflating: jre1.5.0_05/lib/zi/Europe/Vaduz
  inflating: jre1.5.0_05/lib/zi/Europe/Belgrade
  inflating: jre1.5.0_05/lib/zi/Europe/Berlin
  inflating: jre1.5.0_05/lib/zi/Europe/Luxembourg
  inflating: jre1.5.0_05/lib/zi/Europe/Oslo
  inflating: jre1.5.0_05/lib/zi/Europe/Uzhgorod
  inflating: jre1.5.0_05/lib/zi/Europe/Istanbul
  inflating: jre1.5.0_05/lib/zi/Europe/Madrid
  inflating: jre1.5.0_05/lib/zi/Europe/Belfast
  inflating: jre1.5.0_05/lib/zi/Europe/Minsk
  inflating: jre1.5.0_05/lib/zi/Europe/Rome
  inflating: jre1.5.0_05/lib/zi/Europe/Warsaw
  inflating: jre1.5.0_05/lib/zi/Europe/Tirane
  inflating: jre1.5.0_05/lib/zi/Europe/Helsinki
  inflating: jre1.5.0_05/lib/zi/Europe/Vilnius
  inflating: jre1.5.0_05/lib/zi/Europe/Stockholm
  inflating: jre1.5.0_05/lib/zi/Europe/Amsterdam
  inflating: jre1.5.0_05/lib/zi/Europe/Prague
  inflating: jre1.5.0_05/lib/zi/Europe/Dublin
  inflating: jre1.5.0_05/lib/zi/Europe/Vienna
  inflating: jre1.5.0_05/lib/zi/Europe/London
  inflating: jre1.5.0_05/lib/zi/Europe/Tallinn
  inflating: jre1.5.0_05/lib/zi/Europe/Kaliningrad
  inflating: jre1.5.0_05/lib/zi/Europe/Samara
  inflating: jre1.5.0_05/lib/zi/Europe/Malta
  inflating: jre1.5.0_05/lib/zi/Europe/Sofia
  inflating: jre1.5.0_05/lib/zi/Europe/Zurich
  inflating: jre1.5.0_05/lib/zi/Europe/Zaporozhye
  inflating: jre1.5.0_05/lib/zi/Europe/Gibraltar
  inflating: jre1.5.0_05/lib/zi/Europe/Budapest
  inflating: jre1.5.0_05/lib/zi/Europe/Simferopol
  inflating: jre1.5.0_05/lib/zi/Europe/Athens
  inflating: jre1.5.0_05/lib/zi/Europe/Copenhagen
  inflating: jre1.5.0_05/lib/zi/Europe/Monaco
  inflating: jre1.5.0_05/lib/zi/Europe/Andorra
  inflating: jre1.5.0_05/lib/zi/Europe/Bucharest
  inflating: jre1.5.0_05/lib/zi/Europe/Brussels
  inflating: jre1.5.0_05/lib/zi/Europe/Kiev
  inflating: jre1.5.0_05/lib/zi/GMT
   creating: jre1.5.0_05/lib/zi/Indian/
 extracting: jre1.5.0_05/lib/zi/Indian/Reunion
 extracting: jre1.5.0_05/lib/zi/Indian/Antananarivo
 extracting: jre1.5.0_05/lib/zi/Indian/Mahe
 extracting: jre1.5.0_05/lib/zi/Indian/Mayotte
 extracting: jre1.5.0_05/lib/zi/Indian/Comoro
 extracting: jre1.5.0_05/lib/zi/Indian/Mauritius
 extracting: jre1.5.0_05/lib/zi/Indian/Kerguelen
 extracting: jre1.5.0_05/lib/zi/Indian/Chagos
 extracting: jre1.5.0_05/lib/zi/Indian/Maldives
 extracting: jre1.5.0_05/lib/zi/Indian/Cocos
 extracting: jre1.5.0_05/lib/zi/Indian/Christmas
  inflating: jre1.5.0_05/lib/zi/MET
   creating: jre1.5.0_05/lib/zi/Pacific/
 extracting: jre1.5.0_05/lib/zi/Pacific/Kosrae
  inflating: jre1.5.0_05/lib/zi/Pacific/Kwajalein
 extracting: jre1.5.0_05/lib/zi/Pacific/Marquesas
  inflating: jre1.5.0_05/lib/zi/Pacific/Port_Moresby
  inflating: jre1.5.0_05/lib/zi/Pacific/Tongatapu
  inflating: jre1.5.0_05/lib/zi/Pacific/Wallis
  inflating: jre1.5.0_05/lib/zi/Pacific/Truk
  inflating: jre1.5.0_05/lib/zi/Pacific/Wake
  inflating: jre1.5.0_05/lib/zi/Pacific/Funafuti
 extracting: jre1.5.0_05/lib/zi/Pacific/Pago_Pago
  inflating: jre1.5.0_05/lib/zi/Pacific/Norfolk
 extracting: jre1.5.0_05/lib/zi/Pacific/Midway
 extracting: jre1.5.0_05/lib/zi/Pacific/Guadalcanal
  inflating: jre1.5.0_05/lib/zi/Pacific/Tarawa
  inflating: jre1.5.0_05/lib/zi/Pacific/Noumea
 extracting: jre1.5.0_05/lib/zi/Pacific/Fakaofo
  inflating: jre1.5.0_05/lib/zi/Pacific/Fiji
  inflating: jre1.5.0_05/lib/zi/Pacific/Johnston
  inflating: jre1.5.0_05/lib/zi/Pacific/Kiritimati
 extracting: jre1.5.0_05/lib/zi/Pacific/Ponape
  inflating: jre1.5.0_05/lib/zi/Pacific/Enderbury
  inflating: jre1.5.0_05/lib/zi/Pacific/Guam
  inflating: jre1.5.0_05/lib/zi/Pacific/Majuro
 extracting: jre1.5.0_05/lib/zi/Pacific/Niue
 extracting: jre1.5.0_05/lib/zi/Pacific/Tahiti
  inflating: jre1.5.0_05/lib/zi/Pacific/Rarotonga
 extracting: jre1.5.0_05/lib/zi/Pacific/Palau
  inflating: jre1.5.0_05/lib/zi/Pacific/Chatham
  inflating: jre1.5.0_05/lib/zi/Pacific/Auckland
 extracting: jre1.5.0_05/lib/zi/Pacific/Pitcairn
 extracting: jre1.5.0_05/lib/zi/Pacific/Yap
 extracting: jre1.5.0_05/lib/zi/Pacific/Gambier
 extracting: jre1.5.0_05/lib/zi/Pacific/Apia
  inflating: jre1.5.0_05/lib/zi/Pacific/Efate
  inflating: jre1.5.0_05/lib/zi/Pacific/Saipan
 extracting: jre1.5.0_05/lib/zi/Pacific/Nauru
 extracting: jre1.5.0_05/lib/zi/Pacific/Honolulu
  inflating: jre1.5.0_05/lib/zi/Pacific/Easter
 extracting: jre1.5.0_05/lib/zi/Pacific/Galapagos
  inflating: jre1.5.0_05/lib/zi/WET
  inflating: jre1.5.0_05/lib/zi/ZoneInfoMappings
  inflating: jre1.5.0_05/lib/fontconfig.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.9.0.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.8.0.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.2.1.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.3.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.Sun.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.Sun.2003.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.Turbo.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.Turbo.8.0.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.SuSE.properties.src
  inflating: jre1.5.0_05/lib/fontconfig.bfc
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.bfc
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.9.0.bfc
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.8.0.bfc
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.2.1.bfc
  inflating: jre1.5.0_05/lib/fontconfig.RedHat.3.bfc
  inflating: jre1.5.0_05/lib/fontconfig.Sun.bfc
  inflating: jre1.5.0_05/lib/fontconfig.Sun.2003.bfc
  inflating: jre1.5.0_05/lib/fontconfig.Turbo.bfc
  inflating: jre1.5.0_05/lib/fontconfig.Turbo.8.0.bfc
  inflating: jre1.5.0_05/lib/fontconfig.SuSE.bfc
   creating: jre1.5.0_05/lib/cmm/
  inflating: jre1.5.0_05/lib/cmm/sRGB.pf
  inflating: jre1.5.0_05/lib/cmm/GRAY.pf
  inflating: jre1.5.0_05/lib/cmm/CIEXYZ.pf
  inflating: jre1.5.0_05/lib/cmm/PYCC.pf
  inflating: jre1.5.0_05/lib/cmm/LINEAR_RGB.pf
  inflating: jre1.5.0_05/lib/javaws.pack
   creating: jre1.5.0_05/lib/management/
  inflating: jre1.5.0_05/lib/management/management.properties
  inflating: jre1.5.0_05/lib/management/snmp.acl.template
  inflating: jre1.5.0_05/lib/management/jmxremote.password.template
  inflating: jre1.5.0_05/lib/management/jmxremote.access
  inflating: jre1.5.0_05/lib/deploy.pack
   creating: jre1.5.0_05/lib/im/
  inflating: jre1.5.0_05/lib/im/indicim.jar
  inflating: jre1.5.0_05/lib/im/thaiim.jar
  inflating: jre1.5.0_05/lib/rt.pack
   creating: jre1.5.0_05/lib/javaws/
  inflating: jre1.5.0_05/lib/javaws/miniSplash.jpg
  inflating: jre1.5.0_05/lib/javaws/messages.properties
  inflating: jre1.5.0_05/lib/javaws/messages_zh_TW.properties
  inflating: jre1.5.0_05/lib/javaws/messages_de.properties
  inflating: jre1.5.0_05/lib/javaws/messages_es.properties
  inflating: jre1.5.0_05/lib/javaws/messages_fr.properties
  inflating: jre1.5.0_05/lib/javaws/messages_it.properties
  inflating: jre1.5.0_05/lib/javaws/messages_ja.properties
  inflating: jre1.5.0_05/lib/javaws/messages_ko.properties
  inflating: jre1.5.0_05/lib/javaws/messages_sv.properties
  inflating: jre1.5.0_05/lib/javaws/messages_zh_CN.properties
  inflating: jre1.5.0_05/lib/javaws/messages_zh_HK.properties
  inflating: jre1.5.0_05/lib/javaws/Java1.5.ico
  inflating: jre1.5.0_05/lib/jsse.pack
  inflating: jre1.5.0_05/lib/charsets.pack
  inflating: jre1.5.0_05/CHANGES
  inflating: jre1.5.0_05/COPYRIGHT
  inflating: jre1.5.0_05/Welcome.html
  inflating: jre1.5.0_05/README
  inflating: jre1.5.0_05/LICENSE
  inflating: jre1.5.0_05/THIRDPARTYLICENSEREADME.txt
   creating: jre1.5.0_05/man/
   creating: jre1.5.0_05/man/man1/
  inflating: jre1.5.0_05/man/man1/java.1
  inflating: jre1.5.0_05/man/man1/keytool.1
  inflating: jre1.5.0_05/man/man1/rmid.1
  inflating: jre1.5.0_05/man/man1/rmiregistry.1
  inflating: jre1.5.0_05/man/man1/tnameserv.1
  inflating: jre1.5.0_05/man/man1/servertool.1
  inflating: jre1.5.0_05/man/man1/orbd.1
  inflating: jre1.5.0_05/man/man1/policytool.1
  inflating: jre1.5.0_05/man/man1/pack200.1
  inflating: jre1.5.0_05/man/man1/unpack200.1
  inflating: jre1.5.0_05/man/man1/javaws.1
  inflating: jre1.5.0_05/man/man1/kinit.1
  inflating: jre1.5.0_05/man/man1/klist.1
  inflating: jre1.5.0_05/man/man1/ktab.1
    linking: jre1.5.0_05/man/ja      -> ja_JP.eucJP
   creating: jre1.5.0_05/man/ja_JP.eucJP/
   creating: jre1.5.0_05/man/ja_JP.eucJP/man1/
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/java.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/keytool.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/rmid.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/rmiregistry.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/tnameserv.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/servertool.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/orbd.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/policytool.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/pack200.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/unpack200.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/javaws.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/kinit.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/klist.1
  inflating: jre1.5.0_05/man/ja_JP.eucJP/man1/ktab.1
   creating: jre1.5.0_05/plugin/
   creating: jre1.5.0_05/plugin/i386/
   creating: jre1.5.0_05/plugin/i386/ns7/
  inflating: jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
   creating: jre1.5.0_05/plugin/i386/ns7-gcc29/
  inflating: jre1.5.0_05/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
   creating: jre1.5.0_05/plugin/desktop/
 extracting: jre1.5.0_05/plugin/desktop/sun_java.png
  inflating: jre1.5.0_05/plugin/desktop/sun_java.desktop
   creating: jre1.5.0_05/javaws/
    linking: jre1.5.0_05/javaws/javaws  -> ../bin/javaws
Creating jre1.5.0_05/lib/rt.jar
Creating jre1.5.0_05/lib/jsse.jar
Creating jre1.5.0_05/lib/charsets.jar
Creating jre1.5.0_05/lib/ext/localedata.jar
Creating jre1.5.0_05/lib/plugin.jar
Creating jre1.5.0_05/lib/javaws.jar
Creating jre1.5.0_05/lib/deploy.jar
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 285: /etc/mailcap: Permission denied
mkdir: impossibile creare la directory `/usr/share/icons/HighContrast': Permission denied
mkdir: impossibile creare la directory `/usr/share/icons/HighContrastInverse': Permission denied
mkdir: impossibile creare la directory `/usr/share/icons/LowContrast': Permission denied
cp: impossibile creare il file normale `/usr/share/pixmaps/sun-java.png': Permission denied
cp: impossibile creare il file normale `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': No such file or directory
cp: impossibile creare il file normale `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': No such file or directory
cp: impossibile creare il file normale `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': No such file or directory
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 433: /usr/share/mime-info/java-archive.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 434: /usr/share/mime-info/java-archive.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 435: /usr/share/mime-info/java-archive.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 436: /usr/share/mime-info/java-archive.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 437: /usr/share/mime-info/java-archive.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 438: /usr/share/mime-info/java-archive.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 441: /usr/share/mime-info/java-archive.mime: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 442: /usr/share/mime-info/java-archive.mime: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 445: /usr/share/application-registry/java-archive.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 446: /usr/share/application-registry/java-archive.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 447: /usr/share/application-registry/java-archive.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 448: /usr/share/application-registry/java-archive.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 449: /usr/share/application-registry/java-archive.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 450: /usr/share/application-registry/java-archive.applications: Permission denied
mkdir: impossibile creare la directory `/usr/share/icons/HighContrast': Permission denied
mkdir: impossibile creare la directory `/usr/share/icons/HighContrastInverse': Permission denied
mkdir: impossibile creare la directory `/usr/share/icons/LowContrast': Permission denied
cp: impossibile creare il file normale `/usr/share/pixmaps/sun-java.png': Permission denied
cp: impossibile creare il file normale `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': No such file or directory
cp: impossibile creare il file normale `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': No such file or directory
cp: impossibile creare il file normale `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': No such file or directory
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 433: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 434: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 435: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 436: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 437: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 438: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 441: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 442: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 445: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 446: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 447: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 448: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 449: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/silvio/jre-1_5_0_05-linux-i586.bin: line 450: /usr/share/application-registry/java-web-start.applications: Permission denied

Done.

Testing extracted archive... okay.

Create debian package:
    dh_testdir
    dh_testroot
    dh_installchangelogs
    dh_installdocs
    dh_compress
    dh_fixperms
    dh_installdeb
    dh_shlibdeps
    dh_gencontrol
    dh_md5sums
    dh_builddeb
dpkg-deb: costruisco il pacchetto `sun-j2re1.5' in `/tmp/make-jpkg.XXXXFTlmlc/sun-j2re1.5_1.5.0+update05_i386.deb'.
    copy sun-j2re1.5_1.5.0+update05_i386.deb into directory /home/silvio/

The Debian package has been created in the current directory. You can
install the package as root (e.g. dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb).


Removing temporary directory: done
silvio@ubuntu:~$ dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
dpkg: l'operazione richiesta necessita dei privilegi di superuser
silvio@ubuntu:~$ sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
Password:
(Lettura del database ... 69507 file e directory attualmente installati.)
Mi preparo a sostituire sun-j2re1.5 1.5.0+update05 (con sun-j2re1.5_1.5.0+update05_i386.deb) ...
Spacchetto il rimpiazzo di sun-j2re1.5 ...
Configuro sun-j2re1.5 (1.5.0+update05) ...

silvio@ubuntu:~$ java --version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Please help, thanks

Silvio.

---

### Post by michael_salcher on 2005-11-22
try  "sudo update-alternatives --config java" and pick Sun's Java to be executed when you run "java"

---

### Post by SilvioTO on 2005-11-22
your suggested command solved my problem!! Thanks!

Silvio.

---

