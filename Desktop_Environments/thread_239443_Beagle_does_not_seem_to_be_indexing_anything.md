---
title: "Beagle does not seem to be indexing anything"
date: 2006-08-19
forum: Desktop Environments
---

### Post by hansdezwart on 2006-08-19
I have installed Beagle in my Dapper Drake install using apt-get. It has installed the latest package with version number 0.2.6-1ubuntu5. There seemed to be no problems during the installation.

When I do "ps ax | grep "beagle" I get the following output:
```
5359 ?        Sl     0:03 beagled --debug /usr/lib/beagle/BeagleDaemon.exe --bg 
6610 ?        Sl     0:01 beagled-helper --debug /usr/lib/beagle/IndexHelper.exe
12893 pts/0    R+     0:00 grep beagle
```So the deamon seems to be working.

I have also followed up on the installation instructions at [http://beagle-project.org/Ubuntu_Installation](http://beagle-project.org/Ubuntu_Installation) that tell me to uncheck and recheck the box that is next to "Index my home directory" in the preferences dialog.

How come Beagle does not seem to be able to find anything after my computer has been on and idle for days?

Any help or advice would be very much appreciated.

---

### Post by reacocard on 2006-08-19
try running beagled from the command line to force it to index. you could also try adding extended attribute to the partition you're indexing. you'll need to edit the appropriate line in your /etc/fstab like this:
```
/dev/hda9  /home  ext3  defaults,**user_xattr**  0  2
```
the part in bold is what you'll need to add. put in on the partition that contains /home

---

### Post by hansdezwart on 2006-08-21
Thank you for your reaction. I have now changed the attributes in /etc/fstab in the line for my home directory. That seems to give no problems.

When I start "beagled" as a normal user from the commandline I get an error. In the logs I can read that beagled is already started and that I have to start it with "beagled --replace".
If I do that it seems to start fine. But in the log file I see a couple of errors:

This is my output when I do "cat 2006-08-21-11-04-16-Beagle" I get the following output.```
060821 1104168281 05367 Beagle DEBUG: Starting Beagle Daemon (version 0.2.6)
060821 1104168765 05367 Beagle DEBUG: Running on Mono 1.1.13.6
060821 1104168770 05367 Beagle DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --bg
060821 1104171054 05367 Beagle DEBUG: Established a connection to the X server
060821 1104171073 05367 Beagle DEBUG: Starting main loop
060821 1104171150 05367 Beagle DEBUG: Starting messaging server
060821 1104178618 05367 Beagle DEBUG: Starting QueryDriver
060821 1104181138 05367 Beagle DEBUG: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
060821 1104193859 05367 Beagle DEBUG: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
060821 1104194136 05367 Beagle DEBUG: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
060821 1104194438 05367 Beagle DEBUG: Loading Beagle.Util.Conf+NetworkingConfig from networking.xml
060821 1104194503 05367 Beagle DEBUG: Loading Beagle.Util.Conf+WebServicesConfig from webservices.xml
060821 1104194604 05367 Beagle DEBUG: '/usr/lib/beagle/Backends' is not a directory: Nothing loaded from here
060821 1104202372 05367 Beagle DEBUG: Found index helper at /usr/lib/beagle/beagled-index-helper
060821 1104204266 05367 Beagle DEBUG: KMail folders not found. Will keep trying
060821 1104206491 05367 Beagle DEBUG: Starting Inotify Backend
060821 1104305363 05367 Beagle ERROR: Caught exception while instantiating Files backend
060821 1104305377 05367 Beagle ERROR EX: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.IOException: Lock obain timed out: /home/hansdezwart/.beagle/Indexes/FileSystemIndex/Locks/lucene-f5658b12a993dde9c6e4d766d29f9504-commit.lock -- pid  -- process exists
060821 1104305377 05367 Beagle ERROR EX: in [0x0010e] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Store/Lock.cs:91) Lucene.Net.Store.Lock:Obtain (Int64 lockWaitTimeout)
060821 1104305377 05367 Beagle ERROR EX: in [0x0000e] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Store/Lock.cs:144) Lucene.Net.Store.Lock+With:Run ()
060821 1104305377 05367 Beagle ERROR EX: in [0x0001f] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:205) Lucene.Net.Index.IndexReader:Open (Lucene.Net.Store.Directory directory, Boolean closeDirectory)
060821 1104305377 05367 Beagle ERROR EX: in [0x00002] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:197) Lucene.Net.Index.IndexReader:Open (Lucene.Net.Store.Directory directory)
060821 1104305377 05367 Beagle ERROR EX: in [0x0002c] (at /build/buildd/beagle-0.2.6/beagled/LuceneCommon.cs:1452) Beagle.Daemon.LuceneCommon:GetReader (Lucene.Net.Store.Directory directory)
060821 1104305377 05367 Beagle ERROR EX: in [0x00001] (at /build/buildd/beagle-0.2.6/beagled/LuceneCommon.cs:1437) Beagle.Daemon.LuceneCommon:GetSearcher (Lucene.Net.Store.Directory directory)
060821 1104305377 05367 Beagle ERROR EX: in [0x00023] (at /build/buildd/beagle-0.2.6/beagled/FileSystemQueryable/LuceneNameResolver.cs:234) Beagle.Daemon.FileSystemQueryable.LuceneNameResolver:GetAllDirectoryNameInfo ()
060821 1104305377 05367 Beagle ERROR EX: in [0x00006] (at /build/buildd/beagle-0.2.6/beagled/FileSystemQueryable/FileSystemQueryable.cs:296) Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:PreloadDirectoryNameInfo ()
060821 1104305377 05367 Beagle ERROR EX: in [0x000f5] (at /build/buildd/beagle-0.2.6/beagled/FileSystemQueryable/FileSystemQueryable.cs:111) Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:.ctor ()
060821 1104305377 05367 Beagle ERROR EX: in <0x00000> <unknown method>
060821 1104305377 05367 Beagle ERROR EX: in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
060821 1104305377 05367 Beagle ERROR EX: in <0x0008d> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---
060821 1104305377 05367 Beagle ERROR EX:
060821 1104305377 05367 Beagle ERROR EX: in <0x0010e> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
060821 1104305377 05367 Beagle ERROR EX: in <0x0001c> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
060821 1104305377 05367 Beagle ERROR EX: in <0x00035> System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
060821 1104305377 05367 Beagle ERROR EX: in <0x00105> System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
060821 1104305377 05367 Beagle ERROR EX: in <0x0000c> System.Activator:CreateInstance (System.Type type)
060821 1104305377 05367 Beagle ERROR EX: in [0x000e3] (at /build/buildd/beagle-0.2.6/beagled/QueryDriver.cs:176) Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly assembly)
060821 1104307060 05367 Beagle DEBUG: Found 9 backends in /usr/lib/beagle/BeagleDaemonLib.dll
060821 1104307068 05367 Beagle DEBUG: Reading mapping from filters
060821 1104308256 05367 Beagle DEBUG: Loading system static indexes.
060821 1104308438 05367 Beagle DEBUG: Initializing static queryable: /var/cache/beagle/indexes/applications
060821 1104308571 05367 Beagle DEBUG: Initializing static queryable: /var/cache/beagle/indexes/documentation
060821 1104308572 05367 Beagle DEBUG: Found 2 system-wide indexes.
060821 1104308580 05367 Beagle DEBUG: Loading user-configured static indexes.
060821 1104308581 05367 Beagle DEBUG: Found 0 user-configured static indexes..
060821 1104308582 05367 Beagle DEBUG: Waiting 60 seconds before starting queryables
060821 1104308584 05367 Beagle DEBUG: Starting Scheduler thread
060821 1104308590 05367 Beagle DEBUG: Starting Inotify threads
060821 1104308691 05367 Beagle DEBUG: Daemon initialization finished after 13.76s
060821 1104444166 05367 Beagle DEBUG: Server '/home/hansdezwart/.beagle/socket' shut down
060821 1104444181 05367 Beagle DEBUG: Exiting
060821 1104444189 05367 Beagle DEBUG: Leaving BeagleDaemon.Main
```There seem to be a lot of errors...

When I now do "ps ax | grep beagle" I get the following output:[CODE][540 pts/0    Sl     0:02 beagled --debug /usr/lib/beagle/BeagleDaemon.exe --replace --bg
 5687 pts/0    Sl     0:03 beagled-helper --debug /usr/lib/beagle/IndexHelper.exe
 6577 ?        Sl     0:01 beagle-search --debug /usr/lib/beagle/Search.exe
 6599 pts/0    R+     0:00 grep beagle
/CODE]The search.exe is new. Does this mean Beagle is indexing?

Do I have to manually start beagled every time I start my laptop? Or should the extended attributes option kill the need for search.exe to run once it has finished indexing?
Last two questions: Is there a way to check how far the indexing has reached? How do you know that it is done?

I hope somebody can enlighten me :)

---

### Post by hansdezwart on 2006-08-21
OK just some more information. I have take the information in the beagle FAQ to get Beagle to index more quickly:```
$ beagle-shutdown
$ export BEAGLE_EXERCISE_THE_DOG=1
$ beagled
$ beagle-status   # <ctl>C to exit the status utility.
```The output that I get from beagle-status is:```
Every 5.0s: beagle-info --status                        Mon Aug 21 12:23:27 2006
Scheduler:
Count: 12
Status: Executing task
Maintenance 0 (21/08/2006 11:04:45)
Optimize FileSystemIndex



Pending Tasks:
1 Maintenance 0 (21/08/2006 11:04:55)
Optimize GaimLogIndex

2 Maintenance 0 (21/08/2006 11:04:55)
Optimize IndexingServiceIndex

3 Maintenance 0 (21/08/2006 11:04:55)
Optimize AkregatorIndex

4 Maintenance 0 (21/08/2006 11:04:55)
Optimize KopeteIndex

5 Maintenance 0 (21/08/2006 11:05:59)
```and it doesn't seem to change. All I can do with it is type Ctrl-C to abort it.

If I type "beagle-index-info" I get the following output:```
Index information:
Name: KMail
Count: 0
Indexing: False

Name: GaimLog
Count: 0
Indexing: False

Name: IndexingService
Count: 0
Indexing: False

Name: Tomboy
Count: 1
Indexing: False

Name: Blam
Count: 10
Indexing: False

Name: Liferea
Count: 90
Indexing: False

Name: Akregator
Count: 0
Indexing: False

Name: KonquerorHistory
Count: 1
Indexing: False

Name: Kopete
Count: 0
Indexing: False

Name: applications
Count: 228
Indexing: False

Name: documentation
Count: 3583
Indexing: False
```Nothing seems to be indexing!! ](*,) 

What to do next?

---

### Post by reacocard on 2006-08-21
stop beagle, then try deleteing the .beagle directory in your home folder. then start beagle again. this will force beagle to start indexing all over again. also, did you uncheck/recheck the 'index my home directory' box in beagle's preferences yet? for some reason this seems to be nessecary for some people.

---

### Post by hansdezwart on 2006-08-22
Well, deleting ~/.beagle seemed to work for now. I see that beagle is indexing things (however slowly). Thank you for that!

How long does it approximately take for Beagle to index about 10GB (if I give it no priority)?

---

### Post by reacocard on 2006-08-22
I can take a while. It's not really size of file so much as it is number of files. but just leaving your computer on for a few hours should do fine. you can even use the computer while its indexing. I did and it still took only a hour or so. but i didn't have much for it to index.

---

### Post by Jon &quot;Yogi&quot; on 2006-09-04
I have Dapper amd64 and have been getting lots of problems with Beagle.  It won't start, or index, and I have tried using the "beagled --replace" command, deleting the .beagle directory from the home folder, unistalling and reinstalling beagle, and the uncheck/check scan home folder tick, all to no avail. Any ideas are welcome.

Here is the error message when I try to run beagled:

** (/usr/lib/beagle/BeagleDaemon.exe:7886): WARNING **: The following assembly r eferenced from /usr/lib/beagle/Util.dll could not be loaded:
     Assembly:   Mono.Data.SqliteClient    (assemblyref_index=4)
     Version:    1.0.5000.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/beagle).


** (/usr/lib/beagle/BeagleDaemon.exe:7886): WARNING **: Could not load file or a ssembly 'Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyT oken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/beagle/BeagleDaemon.exe:7886): WARNING **: Could not load file or a ssembly 'Mono.Data.SqliteClient, Version=1.0.5000.0, Culture=neutral, PublicKeyT oken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/beagle/BeagleDaemon.exe:7886): WARNING **: The following assembly r eferenced from /usr/lib/beagle/Filters/Filters.dll could not be loaded:
     Assembly:   ICSharpCode.SharpZipLib    (assemblyref_index=7)
     Version:    0.6.0.0
     Public Key: 1b03e6acf1164f73
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/beagle/Filters).


** (/usr/lib/beagle/BeagleDaemon.exe:7886): WARNING **: Could not load file or a ssembly 'ICSharpCode.SharpZipLib, Version=0.6.0.0, Culture=neutral, PublicKeyTok en=1b03e6acf1164f73' or one of its dependencies.

** (/usr/lib/beagle/BeagleDaemon.exe:7886): WARNING **: Could not load file or a ssembly 'ICSharpCode.SharpZipLib, Version=0.6.0.0, Culture=neutral, PublicKeyTok en=1b03e6acf1164f73' or one of its dependencies.

---

### Post by RoyArne on 2006-09-13
I too had a problem with beagle: It refused to index my .pdf files in **~/Documents**, but I managed to solve it today. In *gnome-terminal*, I typed:

**touch ~/Documents/***

and beagle immediately started to index my files!

Of course, this alters the timestamps on all of the files in the Documents directory. But if you don't mind that the timestamps are changed, you could try to "*touch*" all of the files that won't index.

---

