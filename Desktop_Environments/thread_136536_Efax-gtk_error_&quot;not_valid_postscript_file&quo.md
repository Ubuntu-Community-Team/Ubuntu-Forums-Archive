---
title: "Efax-gtk error: &quot;not valid postscript file&quot;"
date: 2006-02-26
forum: Desktop Environments
---

### Post by snick on 2006-02-26
Hello folks.
Recently installed efax.  ( Ubuntu 5.10 )
When attempting to send a fax, rec'd error message:

  " ESP Ghostscript 7.07.1 Unrecoverable error, exit code 1,
      Not valid postscript file. "

This happens regardless of file used :  .txt     or    .odt
Any advice gratefully rec'd.
Thanks, -JS

---

### Post by patrick295767 on 2006-03-01
HI !

Is you fax installed ... I too installed efax & kfax
then I do : 
ls /dev/mode*
  
And I get nothing... 

Lucent of M30 Toshiba, I guess It's not installed ... 

Greetings

---

### Post by linux4me on 2007-01-17
Snick, It has been almost a year since you posted this, but I hate to see a thread without a solution. I was having the same problem and was searching the forums for a cure when I ran across this post. There are probably better ways, but the following approach solves the problem if you are sending directly from eFax. 

eFax is telling you to use a postscript file, so a pdf, txt, etc. won't work. Fortunately, it's easy to convert documents to postscript format using Open Office Word (OO). To do so, you need a postscript printer driver, though you don't have to have a postscript printer.

To install the postscript printer driver in Edgy, click System -> Administration -> Printing, then double-click 'New Printer'. Ubuntu will search the printer database and look for installed printers. If you don't have a printer connected, it will take a while, but be patient and soon you will see the 'Add a Printer' Dialog. Select 'local printer' and 'use another printer by specifying a port', then click Forward. Choose Apple as the manufacturer, and pick one of the Laserwriter printers, which conveniently use an already-installed postscript printer driver. Click Forward, and finish the install with whatever name you want for the printer. 

When you start OO again (restart it if it was open when you added the printer), you will have your newly installed printer as an option in the File -> Print Dialog. Open the document you wish to fax, choose File -> Print. Select the Apple Laserwriter you installed and check the 'Print to file' box. When you click 'Print' the file will be saved to the current directory with a '.ps' extension.

Back in eFax, select the postscript file you just created and you should be able to fax it. 

There is also a way to fax using eFax directly from OO, but I haven't got that set up. Yet...

---

