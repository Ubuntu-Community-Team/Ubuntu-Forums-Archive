---
title: "Unable to log in to KDE 4.1.3 on Intrepid"
date: 2008-11-25
forum: Desktop Environments
---

### Post by frank78 on 2008-11-25
I'm running KDE 4.1.3 on Kubuntu 8.10, and it worked fine for a couple of weeks after the update from Hardy. My problems started a couple of days ago when my system got very slow all of a sudden and had a lot of hard drive activity. 'top' told me that the plasma process had a memory usage of > 2 GB (and growing), so I killed it and tried to restart it manually (that had worked before when I had Plasma crashes).

However, restarting Plasma did not work, and after a reboot, I could not log in to KDE 4.1.3 any more. The KDM login screen appears, and after entering user name & password, the KDE splash screen appears, goes through the icons and disappears, then the KDE login sound is played, and then there's only the grey KDM background left. A notification bubble in the top left corner of the screen tells me that there are updates available, and then the screen turns white, and that's it.

Neither renaming ~/.kde nor creating a new user with an empty home directory helped. The beginning of ~/.xsession-errors is

```

Xsession: X session started for frank at Tue Nov 25 23:31:16 CET 2008                                                                                                               
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory                                                            
Setting IM through im-switch for locale=en_US.                                                                                                                                      
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.                                                                                         
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading                                                                                            
/usr/bin/xmodmap:  1 error encountered, aborting.                                                                                                                                   
kdostartupconfig4(8902) main: Running kdostartupconfig.                                                                                                                             
startkde: Starting up...                                                                                                                                                            
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher                                                                                                                       
kdeinit4: preparing to launch /usr/bin/kded4                                                                                                                                        
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4                                                                                                                                
kbuildsycoca4 running...                                                                                                                                                            
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update                                                                                                                    
kdeinit4: preparing to launch /usr/bin/kcminit_startup                                                                                                                              
kdeinit4: preparing to launch /usr/bin/ksmserver                                                                                                                                    
<unknown program name>(8991)/ KStartupInfo::createNewStartupId: creating:  "kongresszentrum;1227652276;957036;8991_TIME0" : "unnamed app"                                           
kwin(9055) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_ozone.so"  for  "kwin3_ozone"                                                                          
kdeinit4: preparing to launch /usr/bin/plasma                                                                                                                                       
kdeinit4: preparing to launch /usr/bin/knotify4                                                                                                                                     
<unknown program name>(9056)/ checkComposite: Plasma lacks an argb visual 0x0 0                                                                                                     
<unknown program name>(9056)/ checkComposite: Plasma is COMPOSITE-less on 0x8d0b870                                                                                                 
kwin(9055): Couldn't start knotify from knotify4.desktop:  "KDEInit could not launch '/usr/bin/knotify4'."                                                                          

plasma(9056): Communication problem with  "plasma" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

QObject: Do not delete object, 'unnamed', during its event handler!
kdeinit4: preparing to launch /usr/bin/krunner                     
QObject: Do not delete object, 'unnamed', during its event handler!
<unknown program name>(9060)/: Communication problem with  "krunner" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

```
Then some Soprano/Nepomuk stuff which looks unsuspicious follows. .xsession-errors ends with
```

kaccess(9076) kdemain: X server XKB extension major= 1  minor= 0
kbuildsycoca running...
knotify(9059) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
QObject: Do not delete object, 'unnamed', during its event handler!
kmixctrl(9075) Mixer::openIfValid: Mixer::open() detected master:  "PCM:0"
kmixctrl(9075) Mixer::getGlobalMasterMD: Mixer::masterCardDevice() returns 0 (no globalMaster)
kmixctrl(9075) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "ALSA::HDA_ATI_SB:1"  control= "PCM:0"
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
guidance-power-manager(9081): Communication problem with  "guidance-power-manager" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

QObject: Do not delete object, 'unnamed', during its event handler!
<unknown program name>(9090)/: Communication problem with  "kmix" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

Reading package lists... Done
Building dependency tree
Reading state information... Done
QObject: Do not delete object, 'unnamed', during its event handler!

```
Just in case anyone can tell anything from the processes running after the failed login:
```

frank     8813  0.0  0.0   3532   964 ?        Ss   23:31   0:00 /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
frank     8858  0.0  0.0   4740   600 ?        Ss   23:31   0:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/frank/.gnupg/gpg-agent-info-kongresszentrum /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
frank     8859  0.0  0.0   3868   484 ?        Ss   23:31   0:00 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/frank/.gnupg/gpg-agent-info-kongresszentrum /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
frank     8872  0.0  0.0   1844   544 ?        S    23:31   0:00 /bin/sh /usr/bin/startkde
frank     8875  0.0  0.0   3124   680 ?        S    23:31   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
frank     8876  0.1  0.0   2776   976 ?        Ss   23:31   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
frank     8991  0.0  0.2  33444  4992 ?        Ss   23:31   0:00 kdeinit4: kdeinit4 Running...
frank     8993  0.0  0.4  35488  9656 ?        S    23:31   0:00 klauncher
frank     9052  0.0  0.0   1764   368 ?        S    23:31   0:00 kwrapper4 ksmserver
frank     9053  0.1  0.7  76736 14292 ?        Sl   23:31   0:00 ksmserver
frank     9055  0.2  0.8  53932 15788 ?        S    23:31   0:00 kwin
frank     9059  0.4  1.3 146700 25504 ?        Sl   23:31   0:00 /usr/bin/knotify4
frank     9063  0.1  0.5  72776 11568 ?        Sl   23:31   0:00 /usr/bin/nepomukserver
frank     9065  0.0  0.7  44944 14036 ?        S    23:31   0:00 /usr/bin/nepomukservicestub nepomukstorage
frank     9066  0.0  0.4  31320  9472 ?        S    23:31   0:00 /usr/bin/nepomukservicestub nepomukontologyloader
frank     9067  0.0  0.4  31184  8868 ?        S    23:31   0:00 /usr/bin/nepomukservicestub nepomukfilewatch
frank     9076  0.0  0.4  49620  8896 ?        S    23:31   0:00 /usr/bin/kaccess
frank     9080  0.3  1.3  79044 25300 ?        S    23:31   0:00 /usr/bin/python /usr/bin/jockey-kde --check 60
frank     9082  0.5  1.5  83576 29576 ?        S    23:31   0:00 python /usr/bin/printer-applet
frank     9085  2.7  1.8 101420 35144 ?        SN   23:31   0:01 python /usr/bin/update-notifier-kde
frank     9086  0.1  0.6  30724 11684 ?        S    23:31   0:00 /usr/bin/knetworkmanager
frank     9087  0.1  0.7  52836 14120 ?        S    23:31   0:00 /usr/bin/python /usr/bin/kblueplugd
frank     9093  0.0  0.2  25612  5160 ?        Ss   23:31   0:00 kdeinit Running...
frank     9095  0.0  0.5  49444  9960 ?        S    23:31   0:00 /usr/bin/klipper
frank     9097  0.0  0.2  25284  4084 ?        S    23:31   0:00 dcopserver [kdeinit] --nosid --suicide
frank     9100  0.0  0.3  26224  5832 ?        S    23:31   0:00 klauncher [kdeinit] --new-startup
frank     9103  0.0  0.4  27564  8264 ?        S    23:31   0:00 kded [kdeinit] --new-startup

```
My system is still usable because I've got a 'kde-devel' user with a self-compiled svn checkout of the upcoming KDE 4.2. Logging in on a text console and typing
```

X :1 & export DISPLAY=:1
startkde

```
starts a KDE 4.2 session which works fine. I tried running KDE 4.1.3 apps after entering 'sux - frank' in a Konsole, but running apps that try to communicate with DBus on startup like Dolphin abort with
```

"/usr/bin/dolphin(7595)" Error in thread 3051763392 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
<unknown program name>(7594)/: Communication problem with  "dolphin" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

```
Running other apps like Konqueror or running Dolphin with the --nofork argument leads to a segmentation fault with an infinite backtrace that begins with
```

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb5fe08d0 (LWP 7365)]         
0xb7ddf8ec in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt                                             
#0  0xb7ddf8ec in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0xb7de0e5f in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7de1d86 in realloc () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7305f04 in qRealloc () from /usr/lib/libQtCore.so.4
#4  0xb732f045 in QListData::realloc () from /usr/lib/libQtCore.so.4
#5  0xb732f2b3 in QListData::append () from /usr/lib/libQtCore.so.4
#6  0xb7395b6d in ?? () from /usr/lib/libQtCore.so.4
#7  0xb739143c in QIODevice::seek () from /usr/lib/libQtCore.so.4
#8  0xb789f8d8 in seek (this=0x96fc6e8, pos=106164949312) at /build/buildd/kde4libs-4.1.3/kdeui/icons/kpixmapcache.cpp:192
#9  0xb789fcb2 in KPixmapCache::Private::binarySearchKey (this=0x96428e8, stream=@0xbfcdf0f4, key=@0xbfcdf178, start=302)
    at /build/buildd/kde4libs-4.1.3/kdeui/icons/kpixmapcache.cpp:628
#10 0xb789fd7d in KPixmapCache::Private::binarySearchKey (this=0x96428e8, stream=@0xbfcdf0f4, key=@0xbfcdf178, start=302)
    at /build/buildd/kde4libs-4.1.3/kdeui/icons/kpixmapcache.cpp:638
#11 0xb789fd7d in KPixmapCache::Private::binarySearchKey (this=0x96428e8, stream=@0xbfcdf0f4, key=@0xbfcdf178, start=302)
    at /build/buildd/kde4libs-4.1.3/kdeui/icons/kpixmapcache.cpp:638
#12 0xb789fd7d in KPixmapCache::Private::binarySearchKey (this=0x96428e8, stream=@0xbfcdf0f4, key=@0xbfcdf178, start=302)
    at /build/buildd/kde4libs-4.1.3/kdeui/icons/kpixmapcache.cpp:638
...

```
I've looked up the source of the corresponding function:
```

int KPixmapCache::Private::binarySearchKey(QDataStream& stream, const QString& key, int start)
{
    stream.device()->seek(start);

    QString fkey;
    qint32 foffset;
    quint32 timesused, lastused;
    qint32 leftchild, rightchild;
    stream >> fkey >> foffset >> timesused >> lastused >> leftchild >> rightchild;

    if (key < fkey) {
        if (leftchild) {
            return binarySearchKey(stream, key, leftchild);
        }
    } else if (key == fkey) {
        return start;
    } else if (rightchild) {
        return binarySearchKey(stream, key, rightchild);
    }

    return start;
}

```
Line 638 is the one with "return binarySearchKey(stream, key, leftchild);" in it.

My next idea would be to wipe the "/" partition and reinstall Kubuntu. Any idea how I could solve this issue more easily is greatly appreciated :-)

---

### Post by kilmarnock on 2008-11-26
I am facing a similar problem. I can log in and kde starts. But then, the windows have no title bar. There is no alt-tab and an open konsole. If I start another program, I cannot switch back. After some actions of mine, the whole thing crashes. It is difficult to describe. Alt-F2 works sometimes but afterwards I cannot focus back. I attach my .xsessio-errors. I think, either d-bus or plasma crash. The system stays unusable.

I do not want to complain but intrepid feels like windows for me. It is totally misconfigured (did a dist-upgrade of an not-so old previous install). Ok, I am complaining. Wahwah. This is my first action since two hours, and I do not know if I can reboot and everything is like normal again. I did not do anything that makes me sure why it works now.



The following .xsession-errors is from a crash:
```
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
Setting IM through im-switch for locale=de_DE.                                                                          
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.                             
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading                                
/usr/bin/xmodmap:  1 error encountered, aborting.                                                                       
kdostartupconfig4(10794) main: Running kdostartupconfig.                                                                
startkde: Starting up...                                                                                                
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher                                                           
kdeinit4: preparing to launch /usr/bin/kded4                                                                            
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4                                                                    
kbuildsycoca4 running...                                                                                                
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update                                                        
kdeinit4: preparing to launch /usr/bin/kcminit_startup                                                                  
kdeinit4: preparing to launch /usr/bin/ksmserver                                                                        
<unknown program name>(10831)/ KStartupInfo::createNewStartupId: creating:  "moby;1227692961;292409;10831_TIME0" : "unnamed app"
_IceTransmkdir: Owner of /tmp/.ICE-unix should be set to root                                                                   
kwin(10842) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_ozone.so"  for  "kwin3_ozone"                     
kdeinit4: preparing to launch /usr/bin/krunner                                                                                  
kdeinit4: preparing to launch /usr/bin/knotify4                                                                                 
kwin(10842): Couldn't start knotify from knotify4.desktop:  "KDEInit kann „/usr/bin/knotify4“ nicht starten."                   

kdeinit4: preparing to launch /usr/bin/plasma
<unknown program name>(10847)/ checkComposite: Plasma has an argb visual 0xef9ae0 29360129
<unknown program name>(10847)/ checkComposite: Plasma can use COMPOSITE for effects on 0xef1260
QLayout: Attempting to add QLayout "" to Plasma::Dialog "", which already has a layout         
X Error: BadWindow (invalid Window parameter) 3                                                
  Major opcode: 18 (X_ChangeProperty)                                                          
  Resource id:  0x1c0003c                                                                      
kdeinit4: preparing to launch                                                                  
kio_trash(10856) TrashImpl::init: initialization OK, home trash dir:  "/home/homer/.local/share/Trash"
kio_trash(10856) TrashProtocol::listDir: listdir:  KUrl("trash:/")                                    
kdeinit4: preparing to launch /usr/bin/nepomukserver                                                  
kio_trash(10856) idForDevice: major= 8  minor= 10                                                     
kio_trash(10856) TrashImpl::scanTrashDirectories: found  "/mnt/daten/.Trash-1000"  gave it id  8010   
kio_trash(10856) idForDevice: major= 8  minor= 9                                                      
kio_trash(10856) TrashImpl::scanTrashDirectories: found  "/usr/local/.Trash-1000"  gave it id  8009   
```

it does not look to be this similar, but in fact it leads to messages like
```
QObject: Do not delete object, 'unnamed', during its event handler!
guidance-power-manager(9974): Communication problem with  "guidance-power-manager" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "
```
Which is a dbus crash? like you described.

Sorry, this is a lousy bug report.

The trouble started after removing the strigi-daemon. I think strigi is coupled thightly to konqueror / dolphin. Perhaps the trouble is unrelated.
Felix

---

### Post by jpetso on 2009-03-15
Thanks for analyzing the backtrace, that led me to the solution:

```
rm -rf /var/tmp/kdecache-<youruser>/kpc
```

which holds the data for KPixmapCache. Apparently something in that data was b0rked so KPixmapCache crashed, and along with it all applications that use it. (Which includes every application that uses icons, and there's hardly a KDE application that does *not* use icons.)

---

