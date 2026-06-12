---
title: "Unable to Access Jarfile: Yuicompressor?"
date: 2010-08-11
forum: Desktop Environments
---

### Post by linux4me on 2010-08-11
I'm using Lucid 64-bit and trying to use [YUI Compressor]("http://developer.yahoo.com/yui/compressor/#using") to compress some javascript files, but I get the error message "unable to access jarfile."

I used the Ubuntu Software Center to install YUI Compressor and then ran the following command:
```
java -jar yuicompressor-2.4.2.jar -v myfile.js
```
using the version number from Software Center and the directions on the YUI Compressor site, but got the error. I confirmed that YUI Compressor is in the /usr/share folder, but found it was in there as yui-compressor, so I also tried:
```
java -jar yui-compressor-2.4.2.jar -v myfile.js
```
but got the same error. I also tried:
```
java -jar yui-compressor -v myfile.js
```
since that's the way YUI Compressor appears in /usr/bin and /usr/share, but still the same error.

I checked to see if I had the Java runtime installed. Whoops. Nope. I installed it and still got the same error with all three commands above. Thought it might be a permissions issue, so I ran the commands as sudo, but still got the same error.

I've never run a jarfile before. What am I doing wrong?

TIA

---

### Post by linux4me on 2010-08-12
I finally figured this out.

First of all, the only Java runtime I needed was one I think is installed by default in Lucid. It's called "Standard Java or Java compatible Runtime (headless)." So I didn't have to install anything other than YUI Compressor.

The actual problem was that the YUI Compressor instructions for the command line didn't fit the installation in Ubuntu. The version number doesn't have to be in the command, and the path to the executable does. If I weren't such a noob I would have recognized that right off. Now, it's obvious. Ubuntu was trying to tell me what was wrong.

Once you've installed YUI Compressor, the command line to use will vary somewhat depending on where your javascript files are, but basically, it looks like this:
```
java -jar /usr/share/yui-compressor/yui-compressor.jar -v input.js -o output-min.js
``` where "input.js" is the path to and name of your original file and "output-min.js" is the path and name of the file you want YUI Compressor to create. The "-v" just runs it in verbose mode, and the "-0" tells it the following file name is the output file.

---

