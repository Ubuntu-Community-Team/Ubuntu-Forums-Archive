---
title: "Beagle dont index. Look the log!"
date: 2006-10-04
forum: Desktop Environments
---

### Post by LedStyle on 2006-10-04
I installed beagle in my dapper drake. I deselected and reselected that box to search home and added another partition. The beagle daemon start to index but stop. Look the log:

```
ledstyle@ledstyle:~$ beagled --fg
&#65279;Debug: Starting Beagle Daemon (version 0.2.6)
Debug: Running on Mono 1.1.13.6
Debug: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg
Warn: Extended attributes are not supported on this filesystem.  Performance will suffer as a result.
Debug: Established a connection to the X server
Debug: Starting main loop
Debug: Starting messaging server
Debug: Starting QueryDriver
Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
Debug: Loading Beagle.Util.Conf+NetworkingConfig from networking.xml
Debug: Loading Beagle.Util.Conf+WebServicesConfig from webservices.xml
Debug: Found index helper at /usr/lib/beagle/beagled-index-helper
Debug: Found 2 backends in /usr/lib/beagle/Backends/EvolutionBackends.dll
Debug: KMail folders not found. Will keep trying
Debug: Starting Inotify Backend
Debug: Found 10 backends in /usr/lib/beagle/BeagleDaemonLib.dll
Debug: Reading mapping from filters
Debug: Loading system static indexes.
Debug: Found 0 system-wide indexes.
Debug: Loading user-configured static indexes.
Debug: Found 0 user-configured static indexes..
Debug: Waiting 60 seconds before starting queryables
Debug: Starting Scheduler thread
Debug: Starting Inotify threads
Debug: Daemon initialization finished after 1,39s
Debug: Starting queryables
Debug: Starting backend: 'EvolutionDataServer'
Debug: Scanning addressbooks and calendars
Debug: Getting addressbook changes for file:///home/ledstyle/.evolution/addressbook/local/system
Debug: Addressbook file:///home/ledstyle/.evolution/addressbook/local/system: 0 added, 0 changed, 0 removed
Debug: Getting calendar changes for file:///home/ledstyle/.evolution/calendar/local/system
Debug: Calendar file:///home/ledstyle/.evolution/calendar/local/system: 0 added, 0 changed, 0 removed
Debug: Getting calendar changes for contacts:///
Debug: Caught ResponseMessageException: Connection refused
Debug: InnerException is SocketException -- we probably need to launch a helper
Debug: Launching helper process
Debug: IndexHelper PID is 4868
Debug: Calendar contacts:///: 0 added, 0 changed, 0 removed
Debug: Scanned addressbooks and calendars in 1,11s
Debug: Starting backend: 'EvolutionMail'
Debug: Starting backend: 'KMail'
Debug: Starting Evolution mail backend
Debug: Starting backend: 'Files'
Debug: Adding root: /home/ledstyle
Debug: Starting KMail backend
Debug: KMail directories (local mail) /home/ledstyle/.kde/share/apps/kmail/dimap not found, will repoll.
Debug: Starting mail crawl
Debug: Loaded 427 records from /home/ledstyle/.beagle/Indexes/FileSystemIndex/FileAttributesStore.db in 0,031s
Debug: Adding root: /home/ledstyle
Error: Trying to add an existing root: /home/ledstyle
Debug: Adding root: /media/dados
Debug: Done starting FileSystemQueryable
Debug: Starting backend: 'GaimLog'
Debug: Starting backend: 'IndexingService'
Debug: Scanning for files in the IndexingService directory...
Debug: Will index mbox /home/ledstyle/.evolution/mail/local/Sent
Debug: Overall percent is 0
Debug: Will index mbox /home/ledstyle/.evolution/mail/local/Inbox
Debug: Overall percent is 0
Debug: Will index mbox /home/ledstyle/.evolution/mail/local/Outbox
Debug: Overall percent is 0
Debug: Will index mbox /home/ledstyle/.evolution/mail/local/Drafts
Debug: Overall percent is 0
Debug: Indexed 0 Indexing Service items in ,01s
Debug: Starting backend: 'Tomboy'
Debug: Starting backend: 'Blam'
Debug: Scanning Tomboy notes...
Debug: Starting backend: 'Liferea'
Debug: Starting Gaim log backend
Debug: Starting backend: 'Akregator'
Debug: Loaded 21 records from /home/ledstyle/.beagle/Indexes/TomboyIndex/FileAttributesStore.db in 0,004s
Debug: Scanned 21 notes in ,05s
Debug: Starting backend: 'KonquerorHistory'
Debug: Starting backend: 'Kopete'
Debug: Sequence complete!
&#65279;Debug: Starting messaging server
Warn: Unable to set IO priority for process to idle
Debug: IO priority for process set to best effort 7
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/inbox/summary
Debug: Overall percent is 0
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/sent-mail/summary
Debug: Overall percent is 0
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/neomail-trash/summary
Debug: Overall percent is 0
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/.mailboxlist/summary
Debug: Overall percent is 0
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/.cppop.cache/summary
Debug: Overall percent is 0
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/.cppop.cache.msgs/summary
Debug: Overall percent is 0
Debug: Will index summary /home/ledstyle/.evolution/mail/imap/antonio@tuxresources.org@mail.tuxresources.org/folders/spam/summary
Debug: Overall percent is 0
Debug: Mail crawl finished
Debug: Evolution mail driver worker thread done in ,53s
Debug: Loaded 7774 records from /home/ledstyle/.beagle/Indexes/GaimLogIndex/FileAttributesStore.db in 0,343s
Debug: Helper Size: VmRSS=16,4 MB, size=1,00, 0,0%
Debug: Found IndexHelper (4868) in 1,65s
Debug: -calendar://uri-class-sucks/?source-uid=1158900230.20155.11@ledstyle-desktop&comp-uid=20060923T162009Z-7483-1000-1-0@ledstyle
Debug: +calendar://uri-class-sucks/?source-uid=1158900230.20155.11@ledstyle-desktop&comp-uid=20060923T162009Z-7483-1000-1-0@ledstyle
Debug: Loaded 42 filters from /usr/lib/beagle/Filters/Filters.dll
Debug: Helper Size: VmRSS=23,8 MB, size=1,45, 11,2%
Debug: Gaim log backend worker thread done in 5,21s
Debug: Opening mbox Sent
Debug: Sent: Finished indexing 1 messages
Debug: Loaded 8 records from /home/ledstyle/.beagle/Indexes/EvolutionMailIndex/FileAttributesStore.db in 0,000s
Debug: Overall percent is 9,090909
Debug: Sent: indexed 1 messages
Debug: Opening mbox Inbox
Debug: Inbox: Finished indexing 1 messages
Debug: Overall percent is 18,18182
Debug: Inbox: indexed 1 messages
Debug: Opening mbox Outbox
Debug: Outbox: Finished indexing 0 messages
Debug: Overall percent is 27,27273
Debug: Outbox: indexed 0 messages
Debug: Opening mbox Drafts
Debug: Drafts: Finished indexing 0 messages
Debug: Overall percent is 36,36364
Debug: Drafts: indexed 0 messages
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 40
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 44,44444
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 50
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 57,14286
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 66,66666
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 80
Debug: Unable to determine account name for antonio%40tuxresources.org@mail.tuxresources.org
Debug: Overall percent is 100
Debug: -email://local@local/Sent;uid=532
Debug: -email://local@local/Inbox;uid=7185
Debug: +email://local@local/Sent;uid=532
Debug: +email://local@local/Inbox;uid=7185
Debug: Helper Size: VmRSS=25,3 MB, size=1,54, 13,4%
Debug: -email://local@local/Sent;uid=532#1
Debug: -email://local@local/Sent;uid=532#0
Debug: +email://local@local/Sent;uid=532#1
Debug: +email://local@local/Sent;uid=532#0
Debug: Helper Size: VmRSS=25,6 MB, size=1,56, 13,9%
Debug: Done crawling '/home/ledstyle/Photos'
Debug: Done crawling '/home/ledstyle/Musicas'
Debug: Done crawling '/home/ledstyle'
Debug: Done crawling '/home/ledstyle/MyShare'
Debug: Done crawling '/home/ledstyle/Desktop'
Debug: Done crawling '/home/ledstyle/Files/Drivers'
Debug: Done crawling '/media/dados'
Debug: Done crawling '/home/ledstyle/Musicas/Bruce Dickinson'
Debug: Done crawling '/home/ledstyle/Musicas/Cramberries'
Debug: Done crawling '/home/ledstyle/Musicas/Bush'
Debug: Done crawling '/home/ledstyle/Musicas/Coldplay'
Debug: Done crawling '/home/ledstyle/Musicas/Cowting Crows'
Debug: Done crawling '/home/ledstyle/Musicas/Creed'
Debug: Done crawling '/home/ledstyle/Musicas/Eric Clapton'
Debug: Done crawling '/home/ledstyle/Musicas/Eric Clapton & B.B. King'
Debug: Done crawling '/home/ledstyle/Musicas/Evanescence'
Debug: Done crawling '/home/ledstyle/Musicas/Foo Fighters'
Debug: Done crawling '/home/ledstyle/Musicas/Fuel'
Debug: Done crawling '/home/ledstyle/Musicas/Incubus'
Debug: Done crawling '/home/ledstyle/Musicas/Iron Maiden'
Debug: Done crawling '/home/ledstyle/Musicas/Guns N' Roses'
Debug: Done crawling '/home/ledstyle/Musicas/Hoobastank'
Debug: Done crawling '/home/ledstyle/Musicas/Gorilaz'
Debug: -uid:Up5Wdx7qGkybo3yZQa9JhA
Debug: -uid:1RmfUL1uN0aWFu4GCuBM4w
Debug: -uid:xhgPF8cW1Ee93vZKZTZJHg
Debug: -uid:G_wyQH5U_kycK6A8kYHJ7w
Debug: -uid:TXXF+W4rzk+bafgidq4P1A
Debug: -uid:zZsY_5U1IE6LhELkMwTMMA
Debug: -uid:CCXFKkM1BUeyncGhZ8w4eA
Debug: -uid:TK0lTPOh70aR_BvWCJGEvQ
Debug: -uid:L1KleR+KHEq5luHD0koXPg
Debug: -uid:gdiJmE1fcke0ry6umwqW+A
Debug: -uid:fOyJRdBi3keD75_EvLmxLQ
Debug: -uid:IVPG_HR1EU+2GJe1Q8mZCg
Debug: -uid:rFGL2KhG7UiVLP1aiJOIuw
Debug: -uid:XqPnzVKBtkadX6smeY6CLA
Debug: -uid:Iefn8ESMvE6LMhzCwslWOg
Debug: -uid:u9ej5cKhukSmMI8JrIiT9g
Debug: -uid:4woK7NSzRUWzQzwk7Kd_Jg
Debug: -uid:K1ndkBjK0EOU1++nG+MI+Q
Debug: -uid:JcfPyYKajkKFNgOFQEE_ow
Debug: -uid:nfTrpZ4IrUWZkBuFfxVAuA
Debug: -uid:VGQphlDtoEe3Zo+6tub2cw
Debug: -uid:pRbuTL54IUGWTnoTPqYjcQ
Debug: -uid:PdDBttzIK0yT431rgx3UHg
Debug: -uid:N7haDwJ0Zk2_RtjNFju79w
Debug: -uid:Plm+wtJ7mUWRdwbWvd47oA
Debug: -uid:Ss0G7g7ttkyfkP3O_3HemA
Debug: -uid:3RWngrrnMEunGUTI+PBF9A
Debug: -uid:bS+Ka6TPO0i_thuRo1tj_w
Debug: -uid:uBEIGC+Sn0Ofnrzsv+z42Q
Debug: -uid:kMJUeLUUw0yfoC5OIwRH_A
Debug: -uid:Bw5fjC_nDUuusakriH098g
Debug: -uid:zjIfHnmetk+NcqC3oE0f3Q
Debug: -uid:BXKFQrriskKy5GoeZqTfsg
Debug: -uid:0mBTu1lwzE2l4n9C9iL2Xw
Debug: -uid:Xw7U0AQ9dkaQnMthBU2A+Q
Debug: -uid:DP24vdyWE0O5Kn9_lCuH4Q
Debug: -uid:C67XPUsxSEO8DF4SQAZDrw
Debug: -uid:2Jh60vXEJUqc9Y0w5TtbZA
Debug: Helper Size: VmRSS=25,6 MB, size=1,56, 13,9%
Warn: Exception caught while executing Beagle.Daemon.ConnectionHandler:Void HandleConnection()
Warn: System.IO.IOException: Lock obain timed out: /home/ledstyle/.beagle/Indexes/FileSystemIndex/Locks/lucene-4f260377ed48ed1545f107e9a97de6dc-write.lock -- pid  -- process existsin [0x0010e] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Store/Lock.cs:91) Lucene.Net.Store.Lock:Obtain (Int64 lockWaitTimeout)
in [0x0008d] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexWriter.cs:414) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory d, Lucene.Net.Analysis.Analyzer a, Boolean create, Boolean closeDir)
in [0x00005] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexWriter.cs:401) Lucene.Net.Index.IndexWriter:.ctor (Lucene.Net.Store.Directory d, Lucene.Net.Analysis.Analyzer a, Boolean create)
in [0x00293] (at /build/buildd/beagle-0.2.6/beagled/LuceneIndexingDriver.cs:216) Beagle.Daemon.LuceneIndexingDriver:Flush_Unlocked (Beagle.Daemon.IndexerRequest request)
in [0x0000f] (at /build/buildd/beagle-0.2.6/beagled/LuceneIndexingDriver.cs:90) Beagle.Daemon.LuceneIndexingDriver:Flush (Beagle.Daemon.IndexerRequest request)
in [0x00079] (at /build/buildd/beagle-0.2.6/beagled/IndexHelper/RemoteIndexerExecutor.cs:69) Beagle.IndexHelper.RemoteIndexerExecutor:Execute (Beagle.RequestMessage raw_request)
in [0x00232] (at /build/buildd/beagle-0.2.6/beagled/Server.cs:275) Beagle.Daemon.ConnectionHandler:HandleConnection ()
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in [0x0005a] (at /build/buildd/beagle-0.2.6/Util/ExceptionHandlingThread.cs:54) Beagle.Util.ExceptionHandlingThread:ThreadStarted ()
Debug: Helper Size: VmRSS=25,6 MB, size=1,56, 13,9%
```

What can i do to solve this problem?

tks!

---

### Post by LedStyle on 2006-10-04
I uninstalled the beagle-backend-evolution.

Now the beagle indexed much more time but crashes again!

```
Warn: System.IO.IOException: Lock obain timed out: /home/ledstyle/.beagle/Indexes/FileSystemIndex/Locks/lucene-4f260377ed48ed1545f107e9a97de6dc-write.lock -- pid  -- process exists
in [0x0010e] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Store/Lock.cs:91) Lucene.Net.Store.Lock:Obtain (Int64 lockWaitTimeout)
in [0x00039] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:547) Lucene.Net.Index.IndexReader:AquireWriteLock ()
in [0x00014] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:576) Lucene.Net.Index.IndexReader:Delete (Int32 docNum)
in [0x0001f] (at /build/buildd/beagle-0.2.6/beagled/Lucene.Net/Index/IndexReader.cs:605) Lucene.Net.Index.IndexReader:Delete (Lucene.Net.Index.Term term)
in [0x000a4] (at /build/buildd/beagle-0.2.6/beagled/LuceneIndexingDriver.cs:126) Beagle.Daemon.LuceneIndexingDriver:Flush_Unlocked (Beagle.Daemon.IndexerRequest request)
in [0x0000f] (at /build/buildd/beagle-0.2.6/beagled/LuceneIndexingDriver.cs:90) Beagle.Daemon.LuceneIndexingDriver:Flush (Beagle.Daemon.IndexerRequest request)
in [0x00079] (at /build/buildd/beagle-0.2.6/beagled/IndexHelper/RemoteIndexerExecutor.cs:69) Beagle.IndexHelper.RemoteIndexerExecutor:Execute (Beagle.RequestMessage raw_request)
in [0x00232] (at /build/buildd/beagle-0.2.6/beagled/Server.cs:275) Beagle.Daemon.ConnectionHandler:HandleConnection ()
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in [0x0005a] (at /build/buildd/beagle-0.2.6/Util/ExceptionHandlingThread.cs:54) Beagle.Util.ExceptionHandlingThread:ThreadStarted ()
Debug: Helper Size: VmRSS=22,7 MB, size=2,05, 26,2%
```

---

### Post by warjowuch on 2006-10-17
weird behaviour... I can't help with this, sorry but good luck

Maybe if you delete your .beagle folder, so that ik can make a new one... This might help.

---

### Post by koki on 2006-10-18
Hi,

I have been using Beagle w/o problems for several months, but today I noticed it had stopped working: no matter what I try, it does not find anything anymore (the service is running).

Tried uninstalling and reinstalling, but to no avail.

Anyone has a clue of what the problem may be?

---

### Post by kwalo on 2006-10-18
I had my beagle index broken, when my computer crashed.
What I did was```
killall -9 beagled
killall -9 beagled-helper
rm -rf ~/.beagle
```That made beagle to rebuild index and everything works fine for me.

---

### Post by sean on 2006-10-19
My impression is that Beagle as supported in Dapper is really buggy.  I am looking forward to an alternative called Tracker.  It is a freedesktop.org project.

Sean

---

