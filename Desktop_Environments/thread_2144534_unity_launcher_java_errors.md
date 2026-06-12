---
title: "unity launcher java errors"
date: 2013-05-12
forum: Desktop Environments
---

### Post by torches on 2013-05-12
I am able to start mindcrack (mindcraft) server from command line running the script containig the line 

java -Xms512M -Xmx1G -jar ftbserver.jar

but when I created a launcher and executed it I get these errors below
========================================
2013-05-12 21:59:08 [INFO] [ForgeModLoader] Forge Mod Loader version 4.7.35.556 for Minecraft 1.4.7 loading
2013-05-12 21:59:08 [INFO] [ForgeModLoader] Found valid fingerprint for Minecraft Forge. Certificate fingerprint de4cf8a3f3bc15635810044c39240bf96804ea7d
2013-05-12 21:59:09 [INFO] [STDOUT] 210 recipes
2013-05-12 21:59:09 [INFO] [STDOUT] 27 achievements
2013-05-12 21:59:09 [INFO] [Minecraft] Starting minecraft server version 1.4.7
2013-05-12 21:59:09 [INFO] [MinecraftForge] Attempting early MinecraftForge initialization
2013-05-12 21:59:09 [INFO] [STDOUT] MinecraftForge v6.6.2.534 Initialized
2013-05-12 21:59:09 [INFO] [ForgeModLoader] MinecraftForge v6.6.2.534 Initialized
2013-05-12 21:59:10 [INFO] [STDOUT] Replaced 84 ore recipies
2013-05-12 21:59:10 [INFO] [MinecraftForge] Completed early MinecraftForge initialization
2013-05-12 21:59:10 [INFO] [ForgeModLoader] Reading custom logging properties from /home/othman/config/logging.properties
2013-05-12 21:59:10 [OFF] [ForgeModLoader] Logging level for ForgeModLoader logging is set to ALL
2013-05-12 21:59:10 [INFO] [ForgeModLoader] Searching /home/othman/mods for mods
2013-05-12 21:59:10 [INFO] [ForgeModLoader] Forge Mod Loader has identified 4 mods to load
2013-05-12 21:59:10 [INFO] [mcp] Activating mod mcp
2013-05-12 21:59:10 [INFO] [FML] Activating mod FML
2013-05-12 21:59:10 [INFO] [Forge] Activating mod Forge
2013-05-12 21:59:10 [INFO] [mod_EnchantViewServer] Activating mod mod_EnchantViewServer
2013-05-12 21:59:10 [INFO] [STDERR] java.lang.VerifyError: (class: mod_EnchantViewServer, method: serverCustomPayload signature: (Ljh;Ldk;)V) Incompatible argument to function
2013-05-12 21:59:10 [INFO] [STDERR] 	at java.lang.Class.forName0(Native Method)
2013-05-12 21:59:10 [INFO] [STDERR] 	at java.lang.Class.forName(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.common.ModClassLoader.loadBaseModClass(ModClassLoader.java:87)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.common.modloader.ModLoaderModContainer.constructMod(ModLoaderModContainer.java:489)
2013-05-12 21:59:10 [INFO] [STDERR] 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
2013-05-12 21:59:10 [INFO] [STDERR] 	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at java.lang.reflect.Method.invoke(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventHandler.handleEvent(EventHandler.java:69)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.SynchronizedEventHandler.handleEvent(SynchronizedEventHandler.java:45)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventBus.dispatch(EventBus.java:317)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventBus.dispatchQueuedEvents(EventBus.java:300)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventBus.post(EventBus.java:268)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.common.LoadController.propogateStateMessage(LoadController.java:153)
2013-05-12 21:59:10 [INFO] [STDERR] 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
2013-05-12 21:59:10 [INFO] [STDERR] 	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at java.lang.reflect.Method.invoke(Unknown Source)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventHandler.handleEvent(EventHandler.java:69)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.SynchronizedEventHandler.handleEvent(SynchronizedEventHandler.java:45)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventBus.dispatch(EventBus.java:317)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventBus.dispatchQueuedEvents(EventBus.java:300)
2013-05-12 21:59:10 [INFO] [STDERR] 	at com.google.common.eventbus.EventBus.post(EventBus.java:268)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.common.LoadController.distributeStateMessage(LoadController.java:86)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.common.Loader.loadMods(Loader.java:494)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.server.FMLServerHandler.beginServerLoading(FMLServerHandler.java:86)
2013-05-12 21:59:10 [INFO] [STDERR] 	at cpw.mods.fml.common.FMLCommonHandler.onServerStart(FMLCommonHandler.java:351)
2013-05-12 21:59:10 [INFO] [STDERR] 	at ho.c(DedicatedServer.java:64)
2013-05-12 21:59:10 [INFO] [STDERR] 	at net.minecraft.server.MinecraftServer.run(MinecraftServer.java:458)
2013-05-12 21:59:10 [INFO] [STDERR] 	at fy.run(SourceFile:849)
2013-05-12 21:59:10 [SEVERE] [Minecraft] Encountered an unexpected exception VerifyError
java.lang.VerifyError: (class: mod_EnchantViewServer, method: serverCustomPayload signature: (Ljh;Ldk;)V) Incompatible argument to function
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Unknown Source)
	at cpw.mods.fml.common.ModClassLoader.loadBaseModClass(ModClassLoader.java:87)
	at cpw.mods.fml.common.modloader.ModLoaderModContainer.constructMod(ModLoaderModContainer.java:489)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at com.google.common.eventbus.EventHandler.handleEvent(EventHandler.java:69)
	at com.google.common.eventbus.SynchronizedEventHandler.handleEvent(SynchronizedEventHandler.java:45)
	at com.google.common.eventbus.EventBus.dispatch(EventBus.java:317)
	at com.google.common.eventbus.EventBus.dispatchQueuedEvents(EventBus.java:300)
	at com.google.common.eventbus.EventBus.post(EventBus.java:268)
	at cpw.mods.fml.common.LoadController.propogateStateMessage(LoadController.java:153)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at com.google.common.eventbus.EventHandler.handleEvent(EventHandler.java:69)
	at com.google.common.eventbus.SynchronizedEventHandler.handleEvent(SynchronizedEventHandler.java:45)
	at com.google.common.eventbus.EventBus.dispatch(EventBus.java:317)
	at com.google.common.eventbus.EventBus.dispatchQueuedEvents(EventBus.java:300)
	at com.google.common.eventbus.EventBus.post(EventBus.java:268)
	at cpw.mods.fml.common.LoadController.distributeStateMessage(LoadController.java:86)
	at cpw.mods.fml.common.Loader.loadMods(Loader.java:494)
	at cpw.mods.fml.server.FMLServerHandler.beginServerLoading(FMLServerHandler.java:86)
	at cpw.mods.fml.common.FMLCommonHandler.onServerStart(FMLCommonHandler.java:351)
	at ho.c(DedicatedServer.java:64)
	at net.minecraft.server.MinecraftServer.run(MinecraftServer.java:458)
	at fy.run(SourceFile:849)
===================================================
any idea why?

---

