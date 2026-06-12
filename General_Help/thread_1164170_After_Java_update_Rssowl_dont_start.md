---
title: "After Java update Rssowl dont start"
date: 2009-05-19
forum: General Help
---

### Post by chek2fire on 2009-05-19
i dont know what happen with the yesterday java update but i cant run rssowl anymore. When i try to run it in terminal i take this message

> Uncaught Exception. Engine closed.      
[db4o 6.1.501   2009-05-19 19:11:21]     
 Please mail the following to [email]exception@db4o.com[/email]:
 <db4o 6.1.501 stacktrace>                       
java.lang.IllegalArgumentException               
        at com.db4o.internal.btree.Searcher.<init>(Unknown Source)
        at com.db4o.internal.btree.BTreeNode.search(Unknown Source)
        at com.db4o.internal.btree.BTreeNode.search(Unknown Source)
        at com.db4o.internal.btree.BTreeNode.add(Unknown Source)   
        at com.db4o.internal.btree.BTreeNode.add(Unknown Source)   
        at com.db4o.internal.btree.BTree.add(Unknown Source)       
        at com.db4o.internal.classindex.BTreeClassIndexStrategy.internalAdd(Unknown Source)
        at com.db4o.internal.classindex.AbstractClassIndexStrategy.add(Unknown Source)     
        at com.db4o.internal.ClassMetadata.addToIndex1(Unknown Source)                     
        at com.db4o.internal.ClassMetadata.addToIndex1(Unknown Source)                     
        at com.db4o.internal.ClassMetadata.addToIndex(Unknown Source)                      
        at com.db4o.internal.LocalObjectContainer.writeNew(Unknown Source)                 
        at com.db4o.internal.ObjectReference.continueSet(Unknown Source)                   
        at com.db4o.internal.PartialObjectContainer.stillToSet(Unknown Source)             
        at com.db4o.internal.PartialObjectContainer.set3(Unknown Source)                                             
        at com.db4o.internal.PartialObjectContainer.set2(Unknown Source)                                             
        at com.db4o.internal.PartialObjectContainer.setAfterReplication(Unknown Source)                              
        at com.db4o.internal.PartialObjectContainer.setInternal(Unknown Source)                                      
        at com.db4o.internal.PartialObjectContainer.set(Unknown Source)                                              
        at com.db4o.internal.PartialObjectContainer.set(Unknown Source)                                              
        at org.rssowl.core.internal.persist.dao.AbstractPersistableDAO.doSave(AbstractPersistableDAO.java:177)       
        at org.rssowl.core.internal.persist.dao.EntitiesToBeIndexedDAOImpl.doSave(EntitiesToBeIndexedDAOImpl.java:107)                                                                                                                    
        at org.rssowl.core.internal.persist.dao.EntitiesToBeIndexedDAOImpl.doSave(EntitiesToBeIndexedDAOImpl.java:1) 
        at org.rssowl.core.internal.persist.dao.AbstractPersistableDAO.saveAll(AbstractPersistableDAO.java:148)      
        at org.rssowl.core.internal.persist.dao.EntitiesToBeIndexedDAOImpl.saveAll(EntitiesToBeIndexedDAOImpl.java:99)                                                                                                                    
        at org.rssowl.core.internal.persist.dao.AbstractPersistableDAO.save(AbstractPersistableDAO.java:130)         
        at org.rssowl.core.internal.persist.dao.EntitiesToBeIndexedDAOImpl.onDatabaseOpened(EntitiesToBeIndexedDAOImpl.java:51)                                                                                                           
        at org.rssowl.core.internal.persist.dao.AbstractPersistableDAO$1.databaseOpened(AbstractPersistableDAO.java:64)                                                                                                                   
        at org.rssowl.core.internal.persist.service.DBManager.fireDatabaseEvent(DBManager.java:133)                  
        at org.rssowl.core.internal.persist.service.DBManager.createDatabase(DBManager.java:361)                     
        at org.rssowl.core.internal.persist.service.DBManager.startup(DBManager.java:115)                            
        at org.rssowl.core.internal.persist.service.PersistenceServiceImpl.startup(PersistenceServiceImpl.java:54)   
        at org.rssowl.core.internal.InternalOwl.startup(InternalOwl.java:95)                                         
        at org.rssowl.ui.internal.Activator$6.run(Activator.java:199)                                                
        at org.eclipse.jface.operation.ModalContext.runInCurrentThread(ModalContext.java:464)                        
        at org.eclipse.jface.operation.ModalContext.run(ModalContext.java:372)                                       
        at org.eclipse.jface.dialogs.ProgressMonitorDialog.run(ProgressMonitorDialog.java:507)                       
        at org.rssowl.ui.internal.Activator.startCore(Activator.java:218)                                            
        at org.rssowl.ui.internal.Activator.access$1(Activator.java:152)                                             
        at org.rssowl.ui.internal.Activator$3.run(Activator.java:140)                                                
        at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)                                               
        at org.rssowl.ui.internal.Activator.start(Activator.java:138)                                                
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)             
        at java.security.AccessController.doPrivileged(Native Method)                                                
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)    
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)              
        at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)                      
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)                    
        at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)                                 
        at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)                                                                                                                   
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)            
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)      
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:370)               
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:446)            
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:399)                    
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:387)                    
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)            
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)                                                     
        at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:315)                    
        at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)                        
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1274)               
        at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:160)                                                                                                          
        at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:867)
        at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)                                                                                                               
        at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:188)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
        at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
        at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
        at org.eclipse.equinox.launcher.Main.main(Main.java:1212)
 </db4o 6.1.501 stacktrace>
Tue May 19 19:11:21 EEST 2009 - [main] Bundle tracker is not set
[db4o 6.1.501   2009-05-19 19:11:21]
 '/home/spiros/.rssowl2/.metadata/.plugins/org.rssowl.core/rssowl.db' is closed. close() was called or open() failed.

Any idea?

---

### Post by kostkon on 2009-05-19
I assume that your default JVM was *Sun Java* but the update has reverted the default JVM back to *OpenJDK*.

Anyway, open a terminal and give
```
sudo update-alternatives --config java
```
and follow the prompts to set/change the default JVM in your system.

---

### Post by chek2fire on 2009-05-19
I have change with this command the java version but the problem still exist

---

### Post by kostkon on 2009-05-19
Could you try to set the Sun Java as the default JVM again
```
sudo update-java-alternatives -s java-6-sun
```
and see if this will make any difference.

---

### Post by chek2fire on 2009-05-19
I have done and this but nothing happens :( The same message when i try to run it from terminal

---

### Post by chek2fire on 2009-05-19
I fixed it!! :D I have to erase the .rssowl2 hidden folder in my home folder and now is run again :D
Thank you for the help

---

