---
title: "Pls help : installing sphinx search on 64bit ubuntu intrepid"
date: 2009-02-11
forum: General Help
---

### Post by prakashsejwani on 2009-02-11
hi all
I have intel core2duo box with 2gb RAM with 64bit ubuntu intrepid ibex
i am trying to compile install sphinx search 0.9.8.1 on it
i have all the prerequisites installed for compiling the source like
build-essentials etc.
i am able to do ./configure
but make command fails after a while with errors like this

g++ -Wall -g -D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -o spelldump spelldump.o libsphinx.a
-Wl,-Bsymbolic-functions -rdynamic -L/usr/lib/mysql -lmysqlclient -lm -lexpat
-L/usr/local/lib
/usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so: undefined reference to
`wssnrtombs@GLIBC_2.2.5'
collect2: ld returned 1 exit status
make[2]: * [spelldump] Error 1
make[2]: Leaving directory `/home/sachin/downloads/sphinx-0.9.8.1/src'
make[1]: * [all] Error 2
make[1]: Leaving directory `/home/sachin/downloads/sphinx-0.9.8.1/src'
make: * [all-recursive] Error 1

also posing the extensive tail of log with errors for anybody to investigate

i guessed its something to do with GLIBC_2.2.5.
pls help

sachin@arjun:~/downloads/sphinx-0.9.8.1$ make
Making all in src
make[1]: Entering directory `/home/sachin/downloads/sphinx-0.9.8.1/src'
if test -d ../.svn; then svn info .. --xml | perl svnxrev.pl; fi;
make all-am
make[2]: Entering directory `/home/sachin/downloads/sphinx-0.9.8.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinx.o -MD -MP -MF ".deps/sphinx.Tpo" -c -o
sphinx.o sphinx.cpp; \
        then mv -f ".deps/sphinx.Tpo" ".deps/sphinx.Po"; else rm -f ".deps/sphinx.Tpo"; exit 1; fi
sphinxstd.h: In member function ‘virtual bool
CSphIndex_VLN::GetKeywords(CSphVector<CSphKeywordInfo>&, ISphTokenizer*, CSphDict*, const
char*, bool)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h: In member function ‘virtual int CSphIndex_VLN::Build(CSphDict*, const
CSphVector<CSphSource*>&, int, ESphDocinfo)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h: In member function ‘bool CSphHTMLStripper::SetRemovedElements(const char*,
CSphString&)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h: In member function ‘bool CSphHTMLStripper::SetIndexedAttrs(const char*,
CSphString&)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxexcerpt.o -MD -MP -MF
".deps/sphinxexcerpt.Tpo" -c -o sphinxexcerpt.o sphinxexcerpt.cpp; \
        then mv -f ".deps/sphinxexcerpt.Tpo" ".deps/sphinxexcerpt.Po"; else rm -f
        ".deps/sphinxexcerpt.Tpo"; exit 1; fi
sphinxstd.h: In member function ‘void ExcerptGen_c::AddJunk(int, int)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h: In member function ‘char* ExcerptGen_c::BuildExcerpt(const ExcerptQuery_t&,
CSphDict*, ISphTokenizer*)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxquery.o -MD -MP -MF ".deps/sphinxquery.Tpo"
-c -o sphinxquery.o sphinxquery.cpp; \
        then mv -f ".deps/sphinxquery.Tpo" ".deps/sphinxquery.Po"; else rm -f
        ".deps/sphinxquery.Tpo"; exit 1; fi
sphinxquery.cpp: In member function ‘bool
CSphExtendedQueryParser::Parse(CSphExtendedQuery&, const char*, const ISphTokenizer*,
const CSphSchema*, CSphDict*)’:
sphinxquery.cpp:1103: warning: comparison between signed and unsigned integer expressions
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxsoundex.o -MD -MP -MF
".deps/sphinxsoundex.Tpo" -c -o sphinxsoundex.o sphinxsoundex.cpp; \
        then mv -f ".deps/sphinxsoundex.Tpo" ".deps/sphinxsoundex.Po"; else rm -f
        ".deps/sphinxsoundex.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxmetaphone.o -MD -MP -MF
".deps/sphinxmetaphone.Tpo" -c -o sphinxmetaphone.o sphinxmetaphone.cpp; \
        then mv -f ".deps/sphinxmetaphone.Tpo" ".deps/sphinxmetaphone.Po"; else rm -f
        ".deps/sphinxmetaphone.Tpo"; exit 1; fi
sphinxmetaphone.cpp: In function ‘int ProcessCode(int, int, CurrentWord_t&, BYTE*,
BYTE*)’:
sphinxmetaphone.cpp:519: warning: suggest explicit braces to avoid ambiguous ‘else’
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxstemen.o -MD -MP -MF
".deps/sphinxstemen.Tpo" -c -o sphinxstemen.o sphinxstemen.cpp; \
        then mv -f ".deps/sphinxstemen.Tpo" ".deps/sphinxstemen.Po"; else rm -f
        ".deps/sphinxstemen.Tpo"; exit 1; fi
sphinxstemen.cpp: In function ‘void stem_en(BYTE*)’:
sphinxstemen.cpp:266: warning: suggest parentheses around && within ||
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxstemru.o -MD -MP -MF
".deps/sphinxstemru.Tpo" -c -o sphinxstemru.o sphinxstemru.cpp; \
        then mv -f ".deps/sphinxstemru.Tpo" ".deps/sphinxstemru.Po"; else rm -f
        ".deps/sphinxstemru.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxutils.o -MD -MP -MF ".deps/sphinxutils.Tpo"
-c -o sphinxutils.o sphinxutils.cpp; \
        then mv -f ".deps/sphinxutils.Tpo" ".deps/sphinxutils.Po"; else rm -f
        ".deps/sphinxutils.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT md5.o -MD -MP -MF ".deps/md5.Tpo" -c -o md5.o
md5.cpp; \
        then mv -f ".deps/md5.Tpo" ".deps/md5.Po"; else rm -f ".deps/md5.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxstd.o -MD -MP -MF ".deps/sphinxstd.Tpo" -c
-o sphinxstd.o sphinxstd.cpp; \
        then mv -f ".deps/sphinxstd.Tpo" ".deps/sphinxstd.Po"; else rm -f ".deps/sphinxstd.Tpo";
        exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxsort.o -MD -MP -MF ".deps/sphinxsort.Tpo"
-c -o sphinxsort.o sphinxsort.cpp; \
        then mv -f ".deps/sphinxsort.Tpo" ".deps/sphinxsort.Po"; else rm -f
        ".deps/sphinxsort.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT sphinxexpr.o -MD -MP -MF ".deps/sphinxexpr.Tpo"
-c -o sphinxexpr.o sphinxexpr.cpp; \
        then mv -f ".deps/sphinxexpr.Tpo" ".deps/sphinxexpr.Po"; else rm -f
        ".deps/sphinxexpr.Tpo"; exit 1; fi
sphinxstd.h: In member function ‘void ExprParser_t::Optimize(int)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
rm -f libsphinx.a
ar cru libsphinx.a sphinx.o sphinxexcerpt.o sphinxquery.o sphinxsoundex.o
sphinxmetaphone.o sphinxstemen.o sphinxstemru.o sphinxutils.o md5.o sphinxstd.o
sphinxsort.o sphinxexpr.o
ranlib libsphinx.a
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT indexer.o -MD -MP -MF ".deps/indexer.Tpo" -c -o
indexer.o indexer.cpp; \
        then mv -f ".deps/indexer.Tpo" ".deps/indexer.Po"; else rm -f ".deps/indexer.Tpo"; exit
        1; fi
sphinxstd.h: In function ‘int main(int, char)’:
sphinxstd.h:439: warning: assuming signed overflow does not occur when assuming that (X +
c) >= X is always true
g++ -Wall -g -D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -o indexer indexer.o libsphinx.a
-Wl,-Bsymbolic-functions -rdynamic -L/usr/lib/mysql -lmysqlclient -lm -lexpat
-L/usr/local/lib
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT searchd.o -MD -MP -MF ".deps/searchd.Tpo" -c -o
searchd.o searchd.cpp; \
        then mv -f ".deps/searchd.Tpo" ".deps/searchd.Po"; else rm -f ".deps/searchd.Tpo"; exit
        1; fi
searchd.cpp: In function ‘void sphLog(ESphLogLevel, const char*, __va_list_tag*)’:
searchd.cpp:357: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp:361: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp: In function ‘void LogQuery(const CSphQuery&, const CSphQueryResult&)’:
searchd.cpp:2643: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp: In function ‘void HandleCommandUpdate(int, int, InputBuffer_c&, int)’:
searchd.cpp:4118: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp:4121: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp:4126: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp:4127: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp: In function ‘void SeamlessTryToForkPrereader()’:
searchd.cpp:4517: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp:4520: warning: ignoring return value of ‘ssize_t write(int, const void*,
size_t)’, declared with attribute warn_unused_result
searchd.cpp: In function ‘int ServiceMain(int, char)’:
searchd.cpp:5790: warning: ignoring return value of ‘int ftruncate(int, __off64_t)’,
declared with attribute warn_unused_result
g++ -Wall -g -D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -o searchd searchd.o libsphinx.a
-Wl,-Bsymbolic-functions -rdynamic -L/usr/lib/mysql -lmysqlclient -lm -lexpat
-L/usr/local/lib
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT search.o -MD -MP -MF ".deps/search.Tpo" -c -o
search.o search.cpp; \
        then mv -f ".deps/search.Tpo" ".deps/search.Po"; else rm -f ".deps/search.Tpo"; exit 1; fi
search.cpp: In function ‘int main(int, char)’:
search.cpp:176: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t,
FILE*)’, declared with attribute warn_unused_result
g++ -Wall -g -D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -o search search.o libsphinx.a
-Wl,-Bsymbolic-functions -rdynamic -L/usr/lib/mysql -lmysqlclient -lm -lexpat
-L/usr/local/lib
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -DSYSCONFDIR="\"/usr/local/etc\""
-I/usr/local/include -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -Wall -g
-D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -MT spelldump.o -MD -MP -MF ".deps/spelldump.Tpo" -c
-o spelldump.o spelldump.cpp; \
        then mv -f ".deps/spelldump.Tpo" ".deps/spelldump.Po"; else rm -f ".deps/spelldump.Tpo";
        exit 1; fi
g++ -Wall -g -D_FILE_OFFSET_BITS=64 -O3 -DNDEBUG -o spelldump spelldump.o libsphinx.a
-Wl,-Bsymbolic-functions -rdynamic -L/usr/lib/mysql -lmysqlclient -lm -lexpat
-L/usr/local/lib
/usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so: undefined reference to
`wssnrtombs@GLIBC_2.2.5'
collect2: ld returned 1 exit status
make[2]: * [spelldump] Error 1
make[2]: Leaving directory `/home/sachin/downloads/sphinx-0.9.8.1/src'
make[1]: * [all] Error 2
make[1]: Leaving directory `/home/sachin/downloads/sphinx-0.9.8.1/src'
make: * [all-recursive] Error 1

---

