---
title: "can't write to FAT FS w/bash script redirection!!"
date: 2006-06-07
forum: Desktop Environments
---

### Post by ssalman on 2006-06-07
This is a simple one, but I can't get it to work :(. 
   
  I'm writing a script to backup my USB memory key contents to my HDD and then write to a log file on the USB showing that I have last backed it up on computer X at time Y.
   
  The backup part is working great, but I can’t write to my log file. Here is what I’m doing:
   
  
```
#! /bin/bash
  tar ……
  uname –n > /media/USB_MEM_KEY/logfile.log
  date >> /media/USB_MEM_KEY/logfile.log
  

``` 
   
  if I run the same commands from the CLI it works, but in the script I get 

```
: Invalid argument4: /media/USB_MEM_KEY/logfile.log
```    
  I tried with ~/logfile.log instead and it worked, so what is wrong with my USB memory key FS format? Can’t bash scripts write to FAT?
   
  Thanks.

---

### Post by ssalman on 2006-06-08
well I changed my script to write to ~/ and then move the file to my memory key, the file created on ~/ has a strange looking carchter at the end, in the terminal it shows as "?", but my script does not have this, not even a white space after the file name, any idea why is that charachter added? Thanks

---

### Post by ssalman on 2006-06-08
I guess I'll keep talking to my self here until someone drops in ;)

Well I found the problem, it was that I was using nano as my editor, and it actually adds a "^k" charckter at the end of the line, not sure if that's the [CR] character or not, but that's why I was having all that trouble before. my script now works. 

but I would like to learn for my sake why is nano does this, and is nano not suitable for script coding?

---

