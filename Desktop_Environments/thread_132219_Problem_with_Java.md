---
title: "Problem with Java"
date: 2006-02-17
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2006-02-17
When installing a .sh file, I get the following message:
Starting Installer ...
java.lang.NoClassDefFoundError: javax.swing.UIManager
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang12LinkageErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang20NoClassDefFoundErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing9UIManager5getUIEPNS0_10JComponentE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing11JOptionPane8updateUIEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing11JOptionPaneC1EPN4java4lang6ObjectEiiPNS0_4IconEP6JArrayIS5_ES5_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing11JOptionPaneC1EPN4java4lang6ObjectEi (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing11JOptionPane17showMessageDialogEPN4java3awt9ComponentEPNS2_4lang6ObjectEPNS6_6StringEi (/usr/lib/libgcj.so.6.0.0)
   at com.install4j.runtime.installer.Installer.reportExeption(java.lang.Throwable, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at com.install4j.runtime.installer.Installer.main(java.lang.String[]) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._Z18_Jv_CallAnyMethodAPN4java4lang6ObjectEPNS0_5ClassEP10_Jv_MethodbbP6JArrayIS4_EP6jvalueSB_bS4_ (/usr/lib/libgcj.so.6.0.0)
   at ._Z18_Jv_CallAnyMethodAPN4java4lang6ObjectEPNS0_5ClassEP10_Jv_MethodbP6JArrayIS4_EPS7_IS2_ES4_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang7reflect6Method6invokeEPNS0_6ObjectEP6JArrayIS4_E (/usr/lib/libgcj.so.6.0.0)
   at com.exe4j.runtime.LauncherEngine.launch(java.lang.String, java.lang.String[], java.lang.String, java.lang.String, boolean, boolean, java.lang.ClassLoader) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at com.install4j.runtime.Launcher.main(java.lang.String[]) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread9call_mainEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread3runEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_ThreadRunPN4java4lang6ThreadE (/usr/lib/libgcj.so.6.0.0)
   at ._Z11_Jv_RunMainP14_Jv_VMInitArgsPN4java4lang5ClassEPKciPS6_b (/usr/lib/libgcj.so.6.0.0)
   at .main (/usr/lib/libgij.so.6.0.0)
   at .__libc_start_main (/lib/tls/i686/cmov/libc-2.3.5.so)

What should I do to fix this problem?

---

### Post by jrib on 2006-02-18
what are you installing?

---

