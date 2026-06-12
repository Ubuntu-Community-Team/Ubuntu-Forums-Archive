---
title: "SPSS installation problem"
date: 2009-03-26
forum: Education &amp; Science
---

### Post by orduek on 2009-03-26
I installed SPSS16 for linux on my /opt folder. For some reason I deleted the SPSS16 folder from OPT (without normall uninstallation).
Since then, when trying to install using sudo ./setup.bin the installation wizard is going up and says an error occured *null.
when exiting i get these error in the terminal:
```
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getLocalPersistedVariable(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getLocalPersistedVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.getVariable(Unknown Source)
	at com.installshield.database.runtime.impl.ISDatabaseImpl.setVariableValue(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.saveReport(Unknown Source)
	at com.installshield.wizardx.conditions.InstallCheckWizardBeanCondition.evaluateTrueCondition(Unknown Source)
	at com.installshield.wizard.WizardBeanCondition.isMet(Unknown Source)
	at com.installshield.util.ConditionSet.evaluteANDExpression(Unknown Source)
	at com.installshield.util.ConditionSet.isMet(Unknown Source)
	at com.installshield.wizard.WizardBean.conditionsMet(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.accept(Unknown Source)
	at com.installshield.wizard.StandardWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ActiveWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.ConditionalWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.MultiWizardTreeIterator.getNext(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductBean(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductBeanProperty(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getProductBeanProperty(Unknown Source)
	at com.installshield.product.service.product.ProductBeanPropertyMethod.invokeWithValidation(Unknown Source)
	at com.installshield.product.service.product.ProductBeanPropertyMethod.invoke(Unknown Source)
	at com.installshield.util.StringResolver.invokeMethod(Unknown Source)
	at com.installshield.util.FunctionToken.getValue(Unknown Source)
	at com.installshield.util.AbstractStringResolver.mergeTokens(Unknown Source)
	at com.installshield.util.AbstractStringResolver.resolveInternal(Unknown Source)
	at com.installshield.util.StringResolver.resolve(Unknown Source)
	at com.installshield.wizard.service.AbstractWizardServices.resolveString(Unknown Source)
	at com.installshield.ui.controls.swing.SwingContainer.resolveString(Unknown Source)
	at com.installshield.ui.controls.swing.SwingFrame.createFrame(Unknown Source)
	at com.installshield.wizard.swing.SwingWizardUI.createPanel(Unknown Source)
	at com.installshield.wizard.swing.SwingWizardUI.displayCustomDialog(Unknown Source)
	at com.installshield.wizard.swing.SwingWizardUI.currentBeanChanged(Unknown Source)
	at com.installshield.wizard.StandardWizardListener.currentBeanChanged(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
ServiceException: (error code = 200; severity = 0; exception = [java.lang.NullPointerException])
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.registry.GenericRegistryService.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.initializeLocalPersistedVariables(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.loadProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductTree(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductBean(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.getProductBeanProperty(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.getProductBeanProperty(Unknown Source)
	at com.installshield.product.service.product.ProductBeanPropertyMethod.invokeWithValidation(Unknown Source)
	at com.installshield.product.service.product.ProductBeanPropertyMethod.invoke(Unknown Source)
	at com.installshield.util.StringResolver.invokeMethod(Unknown Source)
	at com.installshield.util.FunctionToken.getValue(Unknown Source)
	at com.installshield.util.AbstractStringResolver.mergeTokens(Unknown Source)
	at com.installshield.util.AbstractStringResolver.resolveInternal(Unknown Source)
	at com.installshield.util.StringResolver.resolve(Unknown Source)
	at com.installshield.wizard.service.AbstractWizardServices.resolveString(Unknown Source)
	at com.installshield.ui.controls.swing.SwingContainer.resolveString(Unknown Source)
	at com.installshield.wizard.swing.SwingWizardUI.createPanel(Unknown Source)
	at com.installshield.wizard.swing.SwingWizardUI.displayCustomDialog(Unknown Source)
	at com.installshield.wizard.swing.SwingWizardUI.currentBeanChanged(Unknown Source)
	at com.installshield.wizard.StandardWizardListener.currentBeanChanged(Unknown Source)
	at com.installshield.wizard.Wizard$RunThread.run(Unknown Source)
 

```

any idea?

---

### Post by gunksta on 2009-03-26
That beats the hell out of me. What happens when you:
```
sudo updatedb
```
```
locate spss
```

What output do you get from the second command. This will let you know where else SPSS dug in it's tentacles. Perhaps by removing all of this you can eliminate the error.

---

### Post by gunksta on 2009-03-26
Here are a couple of ideas. Are you running ./setup.bin from the CD? If yes, copy ALL of the contents to a directory on your local system and DOUBLE check that you have the permissions set properly.

Have you upgraded the system since last time you use SPSS? I'm curious to know what version of libstdc you have. I'm pretty sure you MUST have libstdc++5 installed or it's going to be no-dice for you. (And yes, this is statistically significant.)

And, then there is this that I found.

[http://ubuntu4students.wordpress.com/2009/03/05/installing-spss-16-linux-on-ubuntu-810/](http://ubuntu4students.wordpress.com/2009/03/05/installing-spss-16-linux-on-ubuntu-810/)

..............

---

### Post by orduek on 2009-03-27
Thanks.
I used that link to try and install it.
I'm sure its some file or something like that that causes the problem but for now I installed it without "sudo" on my home directory and all is well.
So I think I let this when stay a mystery.
BTW I'm using Ubuntu 9.04 with ext4 as filesystem.

---

### Post by gunksta on 2009-03-27
If you're on 9.04 I would definitely try the libstdc++5 idea. I just looked. I don't have it installed and I'm running 9.04 too. I think I read somewhere that you MUST have ++5 or the installer bin won't work, because that's the version they used to compile the installer (not the app itself which is now Java).

Glad it's working.

---

### Post by orduek on 2009-03-27
ofcourse I had to install this library in order to make it work.
But the mysterious *null error was still there ( only when loading the installation from a sudo command).
Thanks

---

### Post by gunksta on 2009-03-27
weird.

---

