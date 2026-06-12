---
title: "Installing Weft-QDA on Ubuntu 10.04 Lucid"
date: 2010-09-26
forum: Education &amp; Science
---

### Post by sdaau on 2010-09-26
Hi all, 

I haven't worked much with [CAQDAS]("http://en.wikipedia.org/wiki/Computer_Assisted_Qualitative_Data_Analysis_Software") (Computer Assisted Qualitative Data Analysis Software) software, but I may have to - so I looked a bit into open variants, and heard about [Weft QDA - a free, open-source tool for qualitative data analysis]("http://www.pressure.to/qda/") from:
[LIST]
[*] [Software for Qualitative Research: how about social web apps? - Methodspace - home of the Research Methods community]("http://www.methodspace.com/forum/topics/software-for-qualitative?commentId=2289984%3AComment%3A4964")
[*] [CAQDAS, CMS, & translation Packages - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=227823")
[/LIST]

So I decided I give it a try, but since the installation wasn't really straightforward (see for instance their [RubyForge: Weft QDA: Tracker]("http://rubyforge.org/tracker/?atid=2625&group_id=665&func=browse") - it is possible this software is no longer actively maintained), here's my writeup. 

First of all, I'm not much into ruby, there seem to be several versions in Lucid, and it's not exactly clear which one is needed for weft_qda; apparently, 1.8 does it just fine. And that I can say, because I tried the following combination that **does not work**:
```

sudo apt-get install ruby1.9.1 libzlib-ruby irb1.9.1 rubygems1.9.1 libsqlite3-ruby1.9.1 libonig2 libsqlite3-dev libonig-dev ruby1.9.1-dev # oniguruma fails

```and this one as well, which also **fails**:
```

sudo apt-get install ruby1.9 libzlib-ruby irb1.9 rubygems1.9 libsqlite3-ruby1.9.1 libonig2 libsqlite3-dev libonig-dev ruby1.9-dev # oniguruma fails

```So, what ended up **working** for me, is more or less the Debian installation instructions posted on "[Christophe Lejeune - Weft QDA under Linux Debian Lenny]("http://www.squash.ulg.ac.be/software/weft-qda.installation.debian.en.html")" (*note that Ubuntu Lucid seems to install ruby1.8 by default, with the below commands*): 
```

sudo apt-get install ruby libzlib-ruby irb rubygems
sudo apt-get install libsqlite3-ruby libsqlite3-0 libonig2 
sudo apt-get install libwxgtk2.8-0
# dev packages are needed for some of the next installs! 
sudo apt-get install libsqlite3-dev libonig-dev ruby-dev make

sudo gem install wxruby
sudo gem install wx_sugar
sudo gem install oniguruma
sudo gem install sqlite3-ruby
sudo gem install diff-lcs
sudo gem install gettext

wget http://rubyforge.org/frs/download.php/35714/weft_qda-1.9.0.tar.gz
tar xvzf weft_qda-1.9.0.tar.gz

cd weft_qda-1.9.0/
ruby -rubygems weft-qda.rb

```So far so good - because you should be able to see a window start; however, opening a new project will fail with:
```

/usr/lib/ruby/1.8/sqlite3/errors.rb:62:in `check': near "END": syntax error (SQLite3::SQLException)

```Now, this is not a package error or anything - this is a SQL syntax problem (*which is why I suspect it is not maintained - this looks like incompatibility with later versions of SQLite?*). After a bit of debugging, I found that the problematic SQL chunk is: 
```

CREATE TRIGGER insert_doc
  AFTER INSERT ON document
  BEGIN
END;

CREATE TRIGGER delete_doc 
  AFTER DELETE ON document
BEGIN
  DELETE FROM document_attr_value WHERE docid = old.docid;
  DELETE FROM code WHERE docid = old.docid;
  DELETE FROM annotation WHERE docid = old.docid;
END; 

```and after a bit more debugging, it turns out that an empty trigger in SQLite 3 raises a syntax error, that is - the problem is: 
```

CREATE TRIGGER insert_doc
  AFTER INSERT ON document
  BEGIN
END;

```Now, this statement occurs two places in the source code: 
```

weft_qda-1.9.0$ grep -r 'TRIGGER insert_doc' .
...
./lib/weft/backend/sqlite/schema.rb:CREATE TRIGGER insert_doc
...
./share/schema.sql:CREATE TRIGGER insert_doc
...

```And it is, in fact, the one in './share/schema.sql' that we need to change. Unfortunately, Sqlite3 seems quite picky about what sentences go into an insert trigger; see:
[LIST]
[*] [empty trigger causes connection to fail - System.Data.SQLite]("http://sqlite.phxsoftware.com/forums/t/1712.aspx")
[*] [Empty Trigger - Database Forum]("http://dbaspot.com/forums/ibm-db2/75033-empty-trigger.html")
[*] [How to create an empty trigger - dBforums]("http://www.dbforums.com/db2/924889-how-create-empty-trigger.html")
[/LIST]

For instance, trying to 'fake' some dummy commands will *also* raise a syntax error, as in: 
```

CREATE TRIGGER insert_doc
  AFTER INSERT ON document
BEGIN
  CREATE TEMPORARY TABLE dummy; <= syntax error CREATE
  DROP TEMPORARY TABLE dummy;
END;

```... so finally, what seems to work, is to use the following sentence in './share/schema.sql' (and possibly in './lib/weft/backend/sqlite/schema.rb', if you want to make sure):
```

CREATE TRIGGER insert_doc
  AFTER INSERT ON document
  BEGIN
  UPDATE document SET created_date = DATETIME('NOW'),modified_date = DATETIME('NOW') where rowid = new.rowid;
END;

```If after that you run the program with 'ruby -rubygems weft-qda.rb', you should now be able to start it, and create and save a new project. 

[[IMG]http://sdaaubckp.sourceforge.net/post/img/weft-qda-1.9.0.png[/IMG]]("http://sdaaubckp.sourceforge.net/post/img/weft-qda-1.9.0.png")

Then, you can click on "Import" when the 'Documents' dropdown is selected, choose the 'README' as an example, click on 'New' and establish categories (note: the first category node will be root node, and only one root node seems possible) - and then you can doubleclick on 'README' to start the viewer. 

With the viewer started, you can click on category nodes, and then mark a text selection, and then click on "Mark" - this will be shown in yellow afterwards; when you click on individual category nodes, only the respective selections are shown. 
 
You can also select a text region, and click on "Note" - which will open a small textbox that will allow you to enter a note, and will add a small reference hyperlink next to the text. 

Note however, that even after this, I managed to get some crashes by random (say, by right-clicking on an empty document window), so it seems this software may need a bit more work (if still actively maintained). And finally note that the **.qdp** file that Weft-QDA saves in, is nothing but a SQLite3 database file - which can be opened directly in SQLite Database Browser (sudo apt-get install sqlitebrowser). 

Also: note that if you use Unicode characters in your textfiles, you may get a truncated view of the text (missing text) in Mark mode (*apparently, something to do with counting how many bytes come per Unicode character for multi-byte chars*); in this case, you may want to convert your text files to plain ASCII characters first. 

In the end - I'm not yet sure what is the exact intended use of this software; but I sure hope this helps someone :) 

Cheers!

---

### Post by lupa18 on 2010-10-05
Yes is very useful. But to difficult to install and still have lot of busgs.

---

### Post by dulbirakan on 2011-04-01
Thanks, I believe these instructions will come in handy.

---

### Post by RadicalLibre on 2012-06-18
I'm trying with ubuntu 12.04 LTS, but is not working.

---

