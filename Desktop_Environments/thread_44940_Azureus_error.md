---
title: "Azureus error"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Jaivaz on 2005-06-28
When I open Azureus the following shows up in my terminal:
> DEBUG::Tue Jun 28 05:03:35 CDT 2005::com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector::accept_loop()::-1:
    VirtualServerChannelSelector::access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector)::-1,VirtualServerChannelSelector$1::runSupport()::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.lang.NullPointerException
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.accept_loop() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector$1.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.2.so)
DEBUG::Tue Jun 28 05:03:36 CDT 2005::com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector::accept_loop()::-1:
    VirtualServerChannelSelector::access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector)::-1,VirtualServerChannelSelector$1::runSupport()::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.lang.NullPointerException
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.accept_loop() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector$1.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.2.so)
The application '<unknown>' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
root@Kamigawa:/home/horace #


The Debug thing continues over and over and it's the same each time. The Azureus intro then pops up and does not load or do anything else and I have to kill it. Does anyone know how to fix this?

---

### Post by jcooper on 2005-06-28
> java.lang.NullPointerException 
Sounds pretty terminal.

What version of the JRE and Azureus are you using?

---

### Post by Jaivaz on 2005-06-28
> root@Kamigawa:/home/horace # java -version
java version "1.4.2"
gcj-4.0 (GCC) 4.0.1 20050517 (prerelease) (Debian 4.0.0-7ubuntu6~5.04ubp1)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

root@Kamigawa:/home/horace #


And as for Azureus.. from what I can tell it's 2.3.2

---

### Post by Jaivaz on 2005-06-29
A little update, I removed java, JRE, and azureus.. Then reinstalled them all completely.. And I still get the following when opening Azureus:
> 
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/horace/azureus/Azureus2.jar:/home/horace/azureu s/swt.jar:/home/horace/azureus/swt-mozilla.jar:/home/horace/azureus/swt-pi.jar" -Djava.library.path="/home/horace/azureus" -Dazureus.install.path="/home/horace/ azureus" org.gudy.azureus2.ui.swt.Main ''
Warning: -Xms16m not understood. Ignoring.
Warning: -Xmx128m not understood. Ignoring.
DEBUG::Wed Jun 29 08:25:01 CDT 2005
  java.lang.ClassNotFoundException: com.sun.net.ssl.internal.ssl.Provider not fo und in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/horace/azureus/Azureus 2.jar,file:./,file:/home/horace/azureus/swt.jar,file:/home/horace/azureus/swt-mo zilla.jar,file:./,file:/home/horace/azureus/swt-pi.jar,file:./], parent=gnu.gcj. runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6. 0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgc j.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0. 0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() ( Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown S ource)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperti es() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unk nown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Un known Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknow n Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown S ource)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

DEBUG::Wed Jun 29 08:25:02 CDT 2005
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance(java.lang.String) (/usr/lib/libgcj.so.6 .0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExi sts(java.lang.String) (Unknown Source)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() ( Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown S ource)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperti es() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unk nown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Un known Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknow n Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown S ource)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

DEBUG::Wed Jun 29 08:25:02 CDT 2005
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance(java.lang.String) (/usr/lib/libgcj.so.6 .0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExi sts(java.lang.String) (Unknown Source)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() ( Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown S ource)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperti es() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unk nown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Un known Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknow n Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown S ource)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

DEBUG::Wed Jun 29 08:25:02 CDT 2005::com.aelitis.azureus.core.networkmanager.Vir tualServerChannelSelector::accept_loop()::-1:
    VirtualServerChannelSelector::access$1(com.aelitis.azureus.core.networkmanag er.VirtualServerChannelSelector)::-1,VirtualServerChannelSelector$1::runSupport( )::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.lang.NullPointerException
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.accep t_loop() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.acces s$1(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector) (Unkno wn Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector$1.run Support() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.2.so)



---

