---
title: "EVE Online Can't Find runGUI?"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by Raavea on 2008-05-17
Hi guys. I just finished my new computer! So the first thing I've installed, other than some eye candy and updates, is EVE Online. Cuz it's epic. Whilst I realise it isn't supported on ATI cards, I was hoping there might be a slim chance of me being able to do it. I honestly don't think (though I'm not exactly fluent in this sort of error) that it is being caused by my cards (2 ATI Sapphire Radeon HD 2600 Pro) but rather there just seems to be a missing file.

Any advice? I downloaded the .deb, then installed it using the package installer, then I used the Configuration program which downloaded the dat file and then said it was installed and configuring etc. Once all that was over, I tried to open EVE.. And nothing happened. So I thought maybe the configuration had missed something and clicked that again. Again nothing. So I popped open the terminal and this is what happens if I attempt to open EVE:
```
~$ eve
Single-user install...
This is the update checker... 
Running /home/raavea/.cedega/.updater/cedega_updater.py
Traceback (most recent call last):
  File "/home/raavea/.cedega/.updater/cedega_updater.py", line 72, in <module>
    updater_obj = updater.Updater(game_name)
  File "/home/raavea/.cedega/.updater/updater.py", line 68, in __init__
    self.support_contact = misc_updater_utils.get_support_contact(game_name, self.manifest_url)
  File "/home/raavea/.cedega/.updater/misc_updater_utils.py", line 352, in get_support_contact
    fp = urllib.urlopen(manifest_url)
  File "/usr/lib/python2.5/urllib.py", line 82, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.5/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.5/urllib.py", line 325, in open_http
    h.endheaders()
  File "/usr/lib/python2.5/httplib.py", line 860, in endheaders
    self._send_output()
  File "/usr/lib/python2.5/httplib.py", line 732, in _send_output
    self.send(msg)
  File "/usr/lib/python2.5/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.5/httplib.py", line 667, in connect
    socket.SOCK_STREAM):
IOError: [Errno socket error] (-2, 'Name or service not known')
Running... /home/raavea/.cedega/.ui/runGUI
exec: 52: /home/raavea/.cedega/.ui/runGUI: not found
```Can anyone tell me what's actually wrong? Is it a simple missing file or is it truly just because I have ATI in my box?

---

### Post by gjwolfswinkel on 2008-05-17
I can't get it to start at all, after the first install. When trying to start from the command line, I get this very similar error:

me@laptop:/usr/bin$ eve
ARGS are -GAME EveOnline-linux
Looking for log.ini file. No CEDEGA_PATH; trying CEDEGA_UPDATER_PATH.
/usr/lib/eve/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
F1 2008-05-17 22:32:12,270 WARNING Don't forget to set up skins for the game EveOnline-linux
Traceback (most recent call last):
  File "/usr/lib/eve/cedega_installer.py", line 412, in <module>
    installer_obj = CedegaGUI_Installer(is_game, game_name, skip_game_install)
  File "/usr/lib/eve/cedega_installer.py", line 68, in __init__
    self.support_contact = misc_updater_utils.get_support_contact(game_name, self.manifest_url)
  File "/usr/lib/eve/misc_updater_utils.py", line 352, in get_support_contact
    fp = urllib.urlopen(manifest_url)
  File "/usr/lib/python2.5/urllib.py", line 82, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.5/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.5/urllib.py", line 325, in open_http
    h.endheaders()
  File "/usr/lib/python2.5/httplib.py", line 860, in endheaders
    self._send_output()
  File "/usr/lib/python2.5/httplib.py", line 732, in _send_output
    self.send(msg)
  File "/usr/lib/python2.5/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.5/httplib.py", line 667, in connect
    socket.SOCK_STREAM):
IOError: [Errno socket error] (-2, 'Name or service not known')

I wanted to give EVE online a try - help is appreciated :)

---

### Post by kuzushi on 2008-05-18
I thought CCP made a Linux client last patch. Is Cedega still required?

---

### Post by Perfect Storm on 2008-05-18
Cedega (the application) is not required. The linux client is wrapped with cedega engine, but installs natively. You don't pay for the extra service, but it's known that cedega works best with nvidia cards.

---

### Post by gjwolfswinkel on 2008-05-18
For Linux installs, you download a small config and patching tool from [this location]("http://www.eve-online.com/download/linux.asp"), you run that to config the client and download the rest of the software (~700 MB). My problem is that I can't even get this config-and-install tool to start.

---

### Post by Sillywombat on 2008-08-29
Same, cant get the loader to work properly.
It took a while, but i managed to get the game (i think) installed, however, not the cedega GUI, giving me this:
```
~$ eve
Single-user install...
This is the update checker... 
Running /home/al/.cedega/.updater/cedega_updater.py
/home/al/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
/home/al/.cedega/.updater/component_get_gui.py:215: GtkDeprecationWarning: gtk.input_add_full is deprecated, use gobject.io_add_watch instead
  self.input_handler = gtk.input_add_full( self.fp, gtk.gdk.INPUT_READ, self.file_cb )
/home/al/.cedega/.updater/updater.py:725: GtkDeprecationWarning: gtk.input_remove is deprecated, use gobject.source_remove instead
  gtk.input_remove( file_diag.input_handler )
Running... /home/al/.cedega/.ui/runGUI
exec: 52: /home/al/.cedega/.ui/runGUI: not found

```

Now, these 2 missing files which the downloader cant install can be found here:
[http://ccp.vo.llnwd.net/o2/linux/eve-000066-1-GUI-update.tgz](http://ccp.vo.llnwd.net/o2/linux/eve-000066-1-GUI-update.tgz)
[http://ccp.vo.llnwd.net/o2/linux/cedega-engine-eve-000099.i386.cpkg](http://ccp.vo.llnwd.net/o2/linux/cedega-engine-eve-000099.i386.cpkg)
As well as the actual game data file, which the installer has problems getting as well:
[http://www.ausgamers.com/files/details/html/37962](http://www.ausgamers.com/files/details/html/37962)

After spending a while trying to get the GUI to work, i gave up with this:
```
al@al-chaos:~$ ~$ eve
bash: ~$: command not found
al@al-chaos:~$ Single-user install...
bash: Single-user: command not found
al@al-chaos:~$ This is the update checker... 
bash: This: command not found
al@al-chaos:~$ Running /home/al/.cedega/.updater/cedega_updater.py
bash: Running: command not found
al@al-chaos:~$ /home/al/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
bash: /home/al/.cedega/.updater/gddb.py:26:: No such file or directory
al@al-chaos:~$   import gddb_parser
The program 'import' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: import: command not found
al@al-chaos:~$ /home/al/.cedega/.updater/component_get_gui.py:215: GtkDeprecationWarning: gtk.input_add_full is deprecated, use gobject.io_add_watch instead
bash: /home/al/.cedega/.updater/component_get_gui.py:215:: No such file or directory
al@al-chaos:~$   self.input_handler = gtk.input_add_full( self.fp, gtk.gdk.INPUT_READ, self.file_cb )
bash: syntax error near unexpected token `('
al@al-chaos:~$ /home/al/.cedega/.updater/updater.py:725: GtkDeprecationWarning: gtk.input_remove is deprecated, use gobject.source_remove instead
bash: /home/al/.cedega/.updater/updater.py:725:: No such file or directory
al@al-chaos:~$   gtk.input_remove( file_diag.input_handler )
bash: syntax error near unexpected token `file_diag.input_handler'
al@al-chaos:~$ Running... /home/al/.cedega/.ui/runGUI
bash: Running...: command not found
al@al-chaos:~$ exec: 52: /home/al/.cedega/.ui/runGUI: not found
bash: exec:: command not found

```




Personally, i dont understand whats the point of
releasing a game that so many people have problems getting to work.

---

### Post by Perfect Storm on 2008-08-30
> **Sillywombat said:**
> 


Personally, i dont understand whats the point of
releasing a game that so many people have problems getting to work.

Mostly when it comes non-Nvidia cards ;)
AFAIK ATI cards aren't supported.

---

### Post by uhappo on 2008-09-01
I'm trying out the native Eve online for my Ubuntu 64-bit. My graphic card is ATI Mobility Radeon 3450.

I can start the program, but in the beginning
[http://img297.imageshack.us/img297/2711/kuvakaappausom7.png](http://img297.imageshack.us/img297/2711/kuvakaappausom7.png)
Eve crashes, console outputs
```

0004:  Bad stuff: client ignore setting select events for 0x900506fc to 0
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 1
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 0
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 1
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 0
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 1
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 0
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 1
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 0
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 1
0004:  Bad stuff: client ignore setting select events for 0x900506fc to 0

```

So, what could be done?

EDIT: Aargh, so ATI and Eve is gonna be a no-go. So how do I uninstall Eve?

---

