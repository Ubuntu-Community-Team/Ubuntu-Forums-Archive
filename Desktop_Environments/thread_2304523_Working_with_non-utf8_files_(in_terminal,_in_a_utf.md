---
title: "Working with non-utf8 files (in terminal, in a utf8 locale)"
date: 2015-11-27
forum: Desktop Environments
---

### Post by xfaeznimltegstg on 2015-11-27
In Ubuntu variants the locale's encoding is (by default) *utf8*.
One may have a lot of files in *iso8859-1* or any similar iso8859 encoding.

Is it possible to work with these files (in terminal windows)? If so, how?
How are grep, sed, awk, less, sort, diff,.. supposed to work on these files?
Any text showing up is scattered with &#65533; signs. One would like to see proper text, not garbage.
The only way is to do (once) a conversion, for the whole stuff?
In case of a repository, all ***past*** variants have to be transformed too? Sounds a bit risky and/or painful.

I know about *recode*, but first I do not know how could it be used in case for example *grep -r*, and second it would do thousands of file conversions per day (before each file access, and after too) which is pretty much the opposite what I would achieve, i.e. zero conversion.

I know about *locale*s, but I found that if I change my locale's encoding to iso8859-2, then.. I have to convert my filenames too (*convmv*), then.. many desktop applications broke i.e. cannot copy file (to smb location), cannot rename file (insists to give it a utf8 name), filename shows up scattered with garbage (red circle), pressing enter on file does not work (unable to open it with the associated application), etc. So this does not seem to be the way.

---

