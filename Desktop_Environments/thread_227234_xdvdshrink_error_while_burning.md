---
title: "xdvdshrink error while burning"
date: 2006-08-01
forum: Desktop Environments
---

### Post by raul on 2006-08-01
it's my first time using xdvdshrink. it ripped the dvd ok, but when i tried to burn the new dvd i get the error below. any ideas? or is there any other program i can use to burn the new dvd?

thanks!


```


   Ready to start burning the new DVD!

   Hit 'q' to quit or any other key to start burning the new DVD...

   Writing new DVD                           Working!Error!

   DVDShrink has failed!
   Error:
      -> growisofs reported an error writing the new DVD!
   Command run:
      -> growisofs -speed=1 -Z /dev/dvd -dvd-video -V FITZCARRALDO /home/raul/docs/dvdrip/FITZCARRALDO/BUILD/ > /dev/null 2> /home/raul/docs/dvdrip/FITZCARRALDO/growisofsdebug.txt

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   End of command output
   ---------------------------------------

INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
/dev/dvd: pre-formatting blank DVD+RW...
:-( Failed to change write speed: 2770->3324

   See the log file at /home/raul/FITZCARRALDO.log for more information.
   Exiting!


   Thank you for using OzWare!


Hit any key to close terminal and exit!
```

---

