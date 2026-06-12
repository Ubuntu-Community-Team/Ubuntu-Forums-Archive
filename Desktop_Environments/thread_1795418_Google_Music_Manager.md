---
title: "Google Music Manager"
date: 2011-07-02
forum: Desktop Environments
---

### Post by tetebueno on 2011-07-02
Hey. I'm trying to run Google Music Manager under Ubuntu since there's still no Linux version. I've found this [http://www.androidcentral.com/using-google-music-manager-ubuntu-made-easy]("http://www.androidcentral.com/using-google-music-manager-ubuntu-made-easy") which used to work, but now I get this:

```
tete@Data:~/Downloads/gmm2$ env WINEPREFIX="/home/tete/.wine" wine C:\\windows\\command\\start.exe /Unix /home/tete/.wine/dosdevices/c:/users/tete/Start\ Menu/Programs/Music\ Manager/Music\ Manager.lnk
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
tete@Data:~/Downloads/gmm2$ err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\users\\tete\\Local Settings\\Application Data\\Programs\\Google\\MusicManager\\MusicManager.exe" failed, status c0000005

```
(Command is taken from Wine's folder under main menu.)

Any ideas?
I really don't like having to use VirtualBox to have a Wilson XP running with only the GMM uploading music.
Thanks.

---

