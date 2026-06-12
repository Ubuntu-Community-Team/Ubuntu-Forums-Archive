---
title: "Using 'jhead' to organize large batches into firectories fail"
date: 2009-01-23
forum: General Help
---

### Post by kjetilbmoe on 2009-01-23
Dear forum members,

I have been recovering an external harddrive for a friend, and eventually had to use foremost to restore the files. I was thinking of rebuilding a logical directory structure by renaming files with jhead, and putting photos taken on the same day in respective directories. However, this fails completely. I can do any renaming *within* a folder, but I cannot put a slash in the expression - then I just get errors.

I was trying to something like [<this>]("http://www.macosxhints.com/article.php?story=20040324071531479") (I know it's a mac site, but the expresssion should be working, right?):

```
jhead -n'/full/path/to/your_output_directory/%Y/%m_%B/%d-%T' source_dir/*
```

I have checked the folder and file permissions, all are set to 777 for the occasion.

Why is this not working?

To this entry

```
sudo jhead -n'/tmp/bildz/%Y-%m-%d/%H-%M' *
```

... this error is returned for each photo:

```
Error: Couldn't rename '2005-12-24-16-12.jpg' to '/tmp/bildz/2005-12-24/16-12.jpg'

```

---

