---
title: "need egrep regex help to extract URLS from an xml site map file"
date: 2009-04-05
forum: General Help
---

### Post by MountainX on 2009-04-05
I need a little search & replace help.

Here's how far I have gotten.
1. started with a site map file like this:
```
<?xml version="1.0" encoding="utf-8"?>
<!--Created by Devintelligence.com Sitemap Generator-->
<urlset xmlns="http://www.google.com/schemas/sitemap/0.84">
  <url>
    <loc>http://example.com</loc>
    <lastmod>2009-04-04</lastmod>
    <changefreq>daily</changefreq>
    <priority>0.9</priority>
  </url>
```2. got rid of all lines except those with URLs
```
$ cat < example.com.SiteMap.xml | grep '^\s*<loc>' > example.com.UrlList.txt
```result looks like this:
```
    <loc>http://example.com</loc>
    <loc>http://example.com/forums/43.aspx</loc>
    <loc>http://example.com/blogs/300.aspx</loc>
```3. Now I need to get rid of the white space at the beginning of the line and keep just the URL between the opening and closing tags, and output that as a new file.

I tried this:
```
sed -e 's/^\s*<loc>(.*)<\/loc>/\1/g' infile > outfile
```
but it doesn't work:
"sed: -e expression #1, char 27: invalid reference \1 on `s' command's RHS"


My final result should be a file with lines like this:
```

http://example.com
http://example.com/forums/43.aspx
http://example.com/blogs/300.aspx
```

---

### Post by MountainX on 2009-04-05
Solved
```
sed 's/^\s*<loc>\(.*\)<\/loc>/\1/' infile > outfile
```

---

### Post by MountainX on 2009-04-05
Best answer:
[http://www.linuxquestions.org/questions/linux-general-1/how-to-do-search-and-replace-on-a-text-file-need-to-extract-urls-from-a-sitemap-file-717014/#post3499264](http://www.linuxquestions.org/questions/linux-general-1/how-to-do-search-and-replace-on-a-text-file-need-to-extract-urls-from-a-sitemap-file-717014/#post3499264)

All the tasks can be accomplished by a single sed command:
     ```
sed '/<loc>/!d; s/ *<loc>\(.*\)<\/loc>/\1/' file 
```The command **!d** _does not_ delete lines containing <loc>, the substitution command print out the text between the <loc> and </loc> tags.

---

