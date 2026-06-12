---
title: "Matlab on Ubuntu 10.04"
date: 2011-05-19
forum: Education &amp; Science
---

### Post by Neela-chan on 2011-05-19
Hi

I've got a little problem installing Matlab on my Ubuntu 10.04 System. I extracted all the files, made all of them executable because it complained not being able to run a couple of files but there are still strange error messages (see below)...

I had openjdk-6 installed and thought that might be the problem and installed the sun java version but it still doesn't work. All I get is a small picture at the beginning of the setup without any text and then the following error messages.

Does anyone have a clue what this is all about? I already tried to look for guides and had a look at the pdf file included in the Matlab setup files. However in all the descriptions and guides I found there is nothing mentioned about required packages or additional steps. The error pops up as soon as I do ./install :(

```
Preparing installation files ...
Installing ...
Exception in thread "main" com.google.inject.ProvisionException: Guice provision errors:

1) Error in custom provider, java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
  at com.mathworks.wizard.WizardModule.provideDisplayProperties(WizardModule.java:61)
  while locating com.mathworks.instutil.DisplayProperties
  at com.mathworks.wizard.ui.components.ComponentsModule.providePaintStrategy(ComponentsModule.java:72)
  while locating com.mathworks.wizard.ui.components.PaintStrategy
    for parameter 4 at com.mathworks.wizard.ui.components.SwingComponentFactoryImpl.<init>(SwingComponentFactoryImpl.java:109)
  while locating com.mathworks.wizard.ui.components.SwingComponentFactoryImpl
  while locating com.mathworks.wizard.ui.components.SwingComponentFactory
    for parameter 1 at com.mathworks.wizard.ui.WizardUIImpl.<init>(WizardUIImpl.java:64)
  while locating com.mathworks.wizard.ui.WizardUIImpl
  while locating com.mathworks.wizard.ui.WizardUI annotated with @com.google.inject.name.Named(value=BaseWizardUI)
  at com.mathworks.wizard.ui.UIModule.provideWizardUI(UIModule.java:36)
  while locating com.mathworks.wizard.ui.WizardUI
    for parameter 0 at com.mathworks.wizard.ExceptionHandlerImpl.<init>(ExceptionHandlerImpl.java:23)
  while locating com.mathworks.wizard.ExceptionHandlerImpl
  while locating com.mathworks.wizard.ExceptionHandler
Caused by: java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:106)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
	at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
	at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
	at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
	at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
	at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
	at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
	at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
	at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
	at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
	at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
	at com.google.inject.Scopes$1$1.get(Scopes.java:54)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
	at com.google.inject.Scopes$1$1.get(Scopes.java:54)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
	at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
	at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
	at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
	at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
	at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
	at com.google.inject.Scopes$1$1.get(Scopes.java:54)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:804)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.InjectorImpl.getInstance(InjectorImpl.java:793)
	at com.mathworks.wizard.WizardLauncher.startWizard(WizardLauncher.java:156)
	at com.mathworks.wizard.WizardLauncher.start(WizardLauncher.java:73)
	at com.mathworks.wizard.AbstractLauncher.launch(AbstractLauncher.java:27)
	at com.mathworks.wizard.AbstractLauncher.launchStandalone(AbstractLauncher.java:18)
	at com.mathworks.installwizard.Launcher.main(Launcher.java:22)
Caused by: java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:101)
	... 54 more
Caused by: com.mathworks.instutil.JNIException: java.lang.UnsatisfiedLinkError: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libinstutil.so: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libstdc++.so.6: file too short
	at com.mathworks.instutil.NativeUtility.loadNativeLibrary(NativeUtility.java:39)
	at com.mathworks.instutil.NativeUtility.<init>(NativeUtility.java:24)
	at com.mathworks.instutil.DisplayPropertiesImpl.<init>(DisplayPropertiesImpl.java:10)
	at com.mathworks.wizard.WizardModule.provideDisplayProperties(WizardModule.java:69)
	... 59 more
Caused by: java.lang.UnsatisfiedLinkError: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libinstutil.so: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libstdc++.so.6: file too short
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.load0(Unknown Source)
	at java.lang.System.load(Unknown Source)
	at com.mathworks.instutil.NativeUtility.loadNativeLibrary(NativeUtility.java:37)
	... 62 more

2) Error in custom provider, java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
  at com.mathworks.wizard.WizardModule.provideDisplayProperties(WizardModule.java:61)
  while locating com.mathworks.instutil.DisplayProperties
  at com.mathworks.wizard.ui.laf.LookAndFeelModule.provideFontStyleStrategy(LookAndFeelModule.java:34)
  while locating com.mathworks.wizard.ui.laf.FontStyleStrategy
    for parameter 1 at com.mathworks.wizard.ui.laf.FontProviderImpl.<init>(FontProviderImpl.java:18)
  while locating com.mathworks.wizard.ui.laf.FontProviderImpl
  while locating com.mathworks.wizard.ui.laf.FontProvider
  at com.mathworks.wizard.ui.laf.LookAndFeelModule.provideUIProperties(LookAndFeelModule.java:41)
  while locating com.mathworks.wizard.ui.laf.UIProperties
    for parameter 3 at com.mathworks.wizard.ui.WizardUIImpl.<init>(WizardUIImpl.java:64)
  while locating com.mathworks.wizard.ui.WizardUIImpl
  while locating com.mathworks.wizard.ui.WizardUI annotated with @com.google.inject.name.Named(value=BaseWizardUI)
  at com.mathworks.wizard.ui.UIModule.provideWizardUI(UIModule.java:36)
  while locating com.mathworks.wizard.ui.WizardUI
    for parameter 0 at com.mathworks.wizard.ExceptionHandlerImpl.<init>(ExceptionHandlerImpl.java:23)
  while locating com.mathworks.wizard.ExceptionHandlerImpl
  while locating com.mathworks.wizard.ExceptionHandler
Caused by: java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:106)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
	at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
	at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
	at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
	at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
	at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
	at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
	at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
	at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
	at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
	at com.google.inject.Scopes$1$1.get(Scopes.java:54)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
	at com.google.inject.Scopes$1$1.get(Scopes.java:54)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
	at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
	at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
	at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
	at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
	at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
	at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
	at com.google.inject.Scopes$1$1.get(Scopes.java:54)
	at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:48)
	at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:758)
	at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:804)
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
	at com.google.inject.InjectorImpl.getInstance(InjectorImpl.java:793)
	at com.mathworks.wizard.WizardLauncher.startWizard(WizardLauncher.java:156)
	at com.mathworks.wizard.WizardLauncher.start(WizardLauncher.java:73)
	at com.mathworks.wizard.AbstractLauncher.launch(AbstractLauncher.java:27)
	at com.mathworks.wizard.AbstractLauncher.launchStandalone(AbstractLauncher.java:18)
	at com.mathworks.installwizard.Launcher.main(Launcher.java:22)
Caused by: java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:101)
	... 61 more
Caused by: com.mathworks.instutil.JNIException: java.lang.UnsatisfiedLinkError: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libinstutil.so: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libstdc++.so.6: file too short
	at com.mathworks.instutil.NativeUtility.loadNativeLibrary(NativeUtility.java:39)
	at com.mathworks.instutil.NativeUtility.<init>(NativeUtility.java:24)
	at com.mathworks.instutil.DisplayPropertiesImpl.<init>(DisplayPropertiesImpl.java:10)
	at com.mathworks.wizard.WizardModule.provideDisplayProperties(WizardModule.java:69)
	... 66 more
Caused by: java.lang.UnsatisfiedLinkError: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libinstutil.so: /home/neela/programs/R2011a-lnx64/bin/glnxa64/libstdc++.so.6: file too short
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.load0(Unknown Source)
	at java.lang.System.load(Unknown Source)
	at com.mathworks.instutil.NativeUtility.loadNativeLibrary(NativeUtility.java:37)
	... 69 more

2 errors
	at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:767)
	at com.google.inject.InjectorImpl.getInstance(InjectorImpl.java:793)
	at com.mathworks.wizard.WizardLauncher.startWizard(WizardLauncher.java:156)
	at com.mathworks.wizard.WizardLauncher.start(WizardLauncher.java:73)
	at com.mathworks.wizard.AbstractLauncher.launch(AbstractLauncher.java:27)
	at com.mathworks.wizard.AbstractLauncher.launchStandalone(AbstractLauncher.java:18)
	at com.mathworks.installwizard.Launcher.main(Launcher.java:22)
Finished

```

---

### Post by physfrank on 2011-05-19
It is my understanding that Matlab comes with a java virtual machine in the installation. That being said, I am having the same problem with my installation, so I am as flummoxed as you.

---

### Post by physfrank on 2011-05-19
Okay, I feel stupid now. The trick is using gksudo instead of sudo to call the script. The root user cannot open graphical applications.

---

### Post by Neela-chan on 2011-05-20
Hmm I will try that thanks! However so far I never had to use sudo at all to install Matlab. It was only needed if you would liked to have the symbolic links as well. Since I don't really need them I never cared much about sudo.

---

### Post by Neela-chan on 2011-05-24
Hmm that didn't solve the problem for me. It doesn't matter whether I do 

./install
sudo ./install
gksudo ./install

there is alsways the same error message as mentioned above... I guess nobody has a clue about what it means or what is wrong?

Using google I found someone at mathworks saying that it is related to symbolic links.
[http://www.mathworks.com/support/solutions/en/data/1-D03Y9K/index.html?solution=1-D03Y9K](http://www.mathworks.com/support/solutions/en/data/1-D03Y9K/index.html?solution=1-D03Y9K)

However I never extracted it on a file system other than ext4 after I downloaded the file from my university server... Could it be that they messed the zip file up and all the symbolic links actually aren't in the compressed file?


####
Edit:

Forget it ;) It is actually not my fault but my university's. They messed the zip files up. I found an old installer zip file which I downloaded a couple of month ago and that one works.

---

### Post by kubumar on 2011-05-30
I'm having the same problem here on Ubuntu 11.04 on Ext2 filesystem. 

Other than Neela-Chan I dont have a install file that works :confused:

@Neela-Chan: Could you maybe provide the file?

Please help - Not even beeing able to install Matlab is suuper annoying.:(:(:(

Kinds
Martin

---

### Post by linuxcrew on 2011-06-01
When the files are zipped, symbolic links are turned into text files. To solve this issue you have to re-create the link using the following commands:

cd bin/glnxa64
rm libstdc++.so.6 && ln -s libstdc++.so.6.0.10 libstdc++.so.6

After that the installer should work.

If you have problems with permissons when accessing the glnxa64 folder (like I had) you have to do a "chmod 755 bin/glnxa64".

Regards
Tobi

---

### Post by sunavch on 2011-07-01
Thats pretty amazing. I have no clue how you figured that out but it works like a charm. Thanks a million.

---

### Post by tommpogg on 2011-07-03
> **Neela-chan said:**
> Hi

I've got a little problem installing Matlab on my Ubuntu 10.04 System. I extracted all the files, made all of them executable because it complained not being able to run a couple of files but there are still strange error messages (see below)...


Are you sure that the installation files are not corrupted?

Normally, sudo ./install works fine

---

### Post by mJayk on 2011-07-05
I used to use matlab on my windows machine switched to Octave when I switched to Ubuntu and reason you dont use Octave?  Just wondering more than anything

---

### Post by bokgeneraal on 2011-08-31
Matlab is easier to learn. It has better builtin help than QtOctave. A nice Windows only Octave graphical frontend is GUI Octave.  Maybe works under wine haven't tried.:P

---

### Post by tommpogg on 2011-09-01
Matlab is more used in the scientific community. As a consequence, there are many toolboxes developped by universities and research groups that are missing on Octave (e.g. CVX for convex optimisation, MPT for optimal constrained control, etc.).
Another feature missing in Octave is Simulink.

The drawback is that you have to pay for all that and you depend completely on the decisions of Mathworks, a private company.

Anyway,  some time ago  I have started a [thread]("http://ubuntuforums.org/showthread.php?t=1799908") about a comparison between Matlab and Octave. I'm telling you, just in case you want to take a look or contribute.

---

### Post by hnkulkarni on 2012-03-04
I did the following as said by Tobi, but I still get the same error as mentioned in the first post. Any help regarding this is highly appreciated, and thanks in advance.

Regards,
Hrushikesh N. Kulkarni

> **linuxcrew said:**
> When the files are zipped, symbolic links are turned into text files. To solve this issue you have to re-create the link using the following commands:

cd bin/glnxa64
rm libstdc++.so.6 && ln -s libstdc++.so.6.0.10 libstdc++.so.6

After that the installer should work.

If you have problems with permissons when accessing the glnxa64 folder (like I had) you have to do a "chmod 755 bin/glnxa64".

Regards
Tobi

---

### Post by thundernet on 2012-04-01
thanks for this your idea "cd bin/glnxa64 rm libstdc++.so.6 && ln -s libstdc++.so.6.0.10 libstdc++.so.6" work great  :) two days i try repair my server and nothing always fail with " file too short"
i try in my ubuntu server 10.10 x64 this, but with little changes, this is not /bin/glnxa64 in 10.10 server, with mc commander copy and paste new libstdc++.so.6 and libstdc++.so.6.0.14 to /usr/lib/ after that use cd /usr/lib/ and rm libstdc++.so.6 && ln -s libstdc++.so.6.0.14 libstdc++.so.6 and apt-get , aptitude dpkg and other instalers start work. yeah great :) and sorry for my english :)

---

### Post by souravc83 on 2012-04-04
I use the matlab's GUI programming (guide) a lot.
that is not possible with octave.
So, I still use Matlab.

---

### Post by joshualai on 2013-02-02
Today is the 2nd day i use Linux in my life. I have spent 48 hours installing MATLAB 2012b on Ubuntu 12.04 inside VirtualBox.

i tried the method above but it did not work, after chmod 755 bin/glnxa64 i am still unable to access the folder. Maybe because i did not mount the shared folder (MATLAB installation file) correctly?

Finally i tried to copy paste the file libstdc++.so.6.0.13 in windows and rename it to libstdc++.so.6 and it works!

Thanks to linuxcrew, your First Cup of Ubuntu is so helpful!

---

