---
title: "Trying to install a program (tacg-4.1.0) from source - but getting errors."
date: 2009-04-12
forum: General Help
---

### Post by Lupusceleri on 2009-04-12
Hello there,

I'm trying to install the program tacg-4.1.0 for my study on my home computer. I got this program from the following page: [http://tacg.sourceforge.net/](http://tacg.sourceforge.net/). However, when trying to get the program setup I'm running into problems. First, I'll show you what I did (and what the terminal spewed out):

```
martijn@MartijnDesktop:~$ tar -xjvf tacg-4.1.0-src.tar.bz2                                                                                                
tacg-4.1.0-src/                                                                                                                                           
tacg-4.1.0-src/Data/                                                                                                                                      
tacg-4.1.0-src/Data/rebase.dam+dcm.data                                                                                                                   
tacg-4.1.0-src/Data/regex.data                                                                                                                            
tacg-4.1.0-src/Data/rebase.dam.data                                                                                                                       
tacg-4.1.0-src/Data/rules.data                                                                                                                            
tacg-4.1.0-src/Data/matrix.data                                                                                                                           
tacg-4.1.0-src/Data/rebase.data                                                                                                                           
tacg-4.1.0-src/Data/rebase.dcm.data                                                                                                                       
tacg-4.1.0-src/Data/codon.data                                                                                                                            
tacg-4.1.0-src/Docs/                                                                                                                                      
tacg-4.1.0-src/Docs/tacg4.man.html                                                                                                                        
tacg-4.1.0-src/Docs/tacg4.help.html                                                                                                                       
tacg-4.1.0-src/Docs/nedit.macros                                                                                                                          
tacg-4.1.0-src/Docs/tacg.1                                                                                                                                
tacg-4.1.0-src/Docs/tacg4.xman.html                                                                                                                       
tacg-4.1.0-src/Docs/tacg4.0.main.html                                                                                                                     
tacg-4.1.0-src/NEWS                                                                                                                                       
tacg-4.1.0-src/Seqs/                                                                                                                                      
tacg-4.1.0-src/Seqs/hsp.cluster.1000.fasta                                                                                                                
tacg-4.1.0-src/Seqs/humanprlreceptor.gb                                                                                                                   
tacg-4.1.0-src/Seqs/humprlrec.pep.fasta                                                                                                                   
tacg-4.1.0-src/Seqs/test.gcg                                                                                                                              
tacg-4.1.0-src/Seqs/test.pir                                                                                                                              
tacg-4.1.0-src/Seqs/test.m-embl                                                                                                                           
tacg-4.1.0-src/Seqs/test.m-ig-b                                                                                                                           
tacg-4.1.0-src/Seqs/test.m-nbrf                                                                                                                           
tacg-4.1.0-src/Seqs/test.m-paup                                                                                                                           
tacg-4.1.0-src/Seqs/test.fasta                                                                                                                            
tacg-4.1.0-src/Seqs/test.fitch                                                                                                                            
tacg-4.1.0-src/Seqs/test.gb                                                                                                                               
tacg-4.1.0-src/Seqs/test.ig                                                                                                                               
tacg-4.1.0-src/Seqs/test.m-msf                                                                                                                            
tacg-4.1.0-src/Seqs/test.m-pir                                                                                                                            
tacg-4.1.0-src/Seqs/humanprlreceptor.gcg                                                                                                                  
tacg-4.1.0-src/Seqs/test.strider                                                                                                                          
tacg-4.1.0-src/Seqs/test.embl                                                                                                                             
tacg-4.1.0-src/Seqs/test.m-gb                                                                                                                             
tacg-4.1.0-src/Seqs/test.m-ig                                                                                                                             
tacg-4.1.0-src/Seqs/test.ig-b                                                                                                                             
tacg-4.1.0-src/Seqs/test.nbrf                                                                                                                             
tacg-4.1.0-src/Seqs/hlef.seq                                                                                                                              
tacg-4.1.0-src/Seqs/test.m-fasta                                                                                                                          
tacg-4.1.0-src/test/                                                                                                                                      
tacg-4.1.0-src/test/testtacg.pl                                                                                                                           
tacg-4.1.0-src/control                                                                                                                                    
tacg-4.1.0-src/SeqFuncs.c                                                                                                                                 
tacg-4.1.0-src/Proximity.c                                                                                                                                
tacg-4.1.0-src/ORF.c                                                                                                                                      
tacg-4.1.0-src/MatrixMatch.c                                                                                                                              
tacg-4.1.0-src/README                                                                                                                                     
tacg-4.1.0-src/configure                                                                                                                                  
tacg-4.1.0-src/seqio.c                                                                                                                                    
tacg-4.1.0-src/seqio.h                                                                                                                                    
tacg-4.1.0-src/configure.in                                                                                                                               
tacg-4.1.0-src/config.guess                                                                                                                               
tacg-4.1.0-src/install-sh                                                                                                                                 
tacg-4.1.0-src/ReadMatrix.c                                                                                                                               
tacg-4.1.0-src/config.sub                                                                                                                                 
tacg-4.1.0-src/missing                                                                                                                                    
tacg-4.1.0-src/mkinstalldirs                                                                                                                              
tacg-4.1.0-src/SlidWin.c                                                                                                                                  
tacg-4.1.0-src/getopt.c                                                                                                                                   
tacg-4.1.0-src/getopt.h                                                                                                                                   
tacg-4.1.0-src/Makefile.am                                                                                                                                
tacg-4.1.0-src/Makefile.in                                                                                                                                
tacg-4.1.0-src/getopt1.c                                                                                                                                  
tacg-4.1.0-src/GelLadSumFrgSits.c                                                                                                                         
tacg-4.1.0-src/Cutting.c                                                                                                                                  
tacg-4.1.0-src/tacg.c                                                                                                                                     
tacg-4.1.0-src/tacg.h                                                                                                                                     
tacg-4.1.0-src/tacgi4/                                                                                                                                    
tacg-4.1.0-src/tacgi4/tacg_Map.pdf                                                                                                                        
tacg-4.1.0-src/tacgi4/form4.html.in                                                                                                                       
tacg-4.1.0-src/tacgi4/tacgi4-cgi.pl.in                                                                                                                    
tacg-4.1.0-src/tacgi4/tacg_web_install.pl                                                                                                                 
tacg-4.1.0-src/tacgi4/microplasmid.gif                                                                                                                    
tacg-4.1.0-src/tacgi4/index.html.in                                                                                                                       
tacg-4.1.0-src/tacgi4/tacg-4.1-banner.gif                                                                                                                 
tacg-4.1.0-src/tacgi4/nedit.macros                                                                                                                        
tacg-4.1.0-src/tacgi4/tacgi4.pl.in                                                                                                                        
tacg-4.1.0-src/AUTHORS                                                                                                                                    
tacg-4.1.0-src/SetFlags.c                                                                                                                                 
tacg-4.1.0-src/RecentFuncs.c                                                                                                                              
tacg-4.1.0-src/INSTALL                                                                                                                                    
tacg-4.1.0-src/ReadEnzFile.c                                                                                                                              
tacg-4.1.0-src/ReadRegex.c                                                                                                                                
tacg-4.1.0-src/ChangeLog                                                                                                                                  
tacg-4.1.0-src/COPYING                                                                                                                                    
tacg-4.1.0-src/strsep.c                                                                                                                                   
tacg-4.1.0-src/strsep.h                                                                                                                                   
tacg-4.1.0-src/COPYRIGHT                                                                                                                                  
martijn@MartijnDesktop:~$ cd tacg-4.1.0-src/
martijn@MartijnDesktop:~/tacg-4.1.0-src$ dir
AUTHORS       configure     COPYRIGHT  GelLadSumFrgSits.c  INSTALL      MatrixMatch.c  ORF.c          README         seqio.c     SlidWin.c  tacg.h
ChangeLog     configure.in  Cutting.c  getopt1.c           install-sh   missing        Proximity.c    ReadRegex.c    seqio.h     strsep.c   tacgi4
config.guess  control       Data       getopt.c            Makefile.am  mkinstalldirs  ReadEnzFile.c  RecentFuncs.c  Seqs        strsep.h   test  
config.sub    COPYING       Docs       getopt.h            Makefile.in  NEWS           ReadMatrix.c   SeqFuncs.c     SetFlags.c  tacg.c           
martijn@MartijnDesktop:~/tacg-4.1.0-src$ ./configure
creating cache ./config.cache                       
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes           
checking whether make sets ${MAKE}... yes                   
checking for working aclocal... missing                     
checking for working autoconf... missing                    
checking for working automake... missing                    
checking for working autoheader... missing                  
checking for working makeinfo... missing                    
checking host system type... x86_64-unknown-linux-gnu       
checking for gcc... gcc                                     
checking whether the C compiler (gcc  ) works... yes        
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes                       
checking whether gcc accepts -g... yes                           
checking for a BSD compatible install... /usr/bin/install -c     
checking whether ln -s works... yes                              
checking for strerror in -lcposix... no                          
checking for st_blksize in struct stat... yes                    
checking for sin in -lm... yes                                   
checking for pcre_exec in -lpcre... yes                          
checking for dirent.h that defines DIR... yes                    
checking for opendir in -ldir... no                              
checking how to run the C preprocessor... gcc -E                 
checking for ANSI C header files... yes                          
checking for fcntl.h... yes                                      
checking for unistd.h... yes                                     
checking for working const... yes                                
checking for pid_t... yes                                        
checking for size_t... yes                                       
checking whether struct tm is in sys/time.h or time.h... time.h  
checking for uid_t in sys/types.h... yes                         
checking for 8-bit clean memcmp... yes                           
checking for unistd.h... (cached) yes                            
checking for getpagesize... yes                                  
checking for working mmap... yes                                 
checking for strftime... yes                                     
checking for vprintf... yes                                      
checking for working alloca.h... yes                             
checking for alloca... yes                                       
checking for putenv... yes                                       
checking for strsep... yes                                       
checking for strdup... yes                                       
checking for strspn... yes                                       
checking for strstr... yes                                       
checking for uname... yes                                        
updating cache ./config.cache                                    
creating ./config.status                                         
creating Makefile                                                
martijn@MartijnDesktop:~/tacg-4.1.0-src$ make                    
gcc -DPACKAGE=\"tacg\" -DVERSION=\"4.1.0\" -DHAVE_ST_BLKSIZE=1 -DHAVE_LIBM=1 -DHAVE_LIBPCRE=1 -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_FCNTL_H=1 -DHAVE_UNISTD_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_STRFTIME=1 -DHAVE_VPRINTF=1 -DHAVE_ALLOCA_H=1 -DHAVE_ALLOCA=1 -DHAVE_PUTENV=1 -DHAVE_STRSEP=1 -DHAVE_STRDUP=1 -DHAVE_STRSPN=1 -DHAVE_STRSTR=1 -DHAVE_UNAME=1  -I. -I. -DBUILD_DATE=\"Sun\ Apr\ 12\ 11:16:56\ CEST\ 2009\" -DUNAME=\"Linux\ MartijnDesktop\ 2.6.27-11-generic\ #1\ SMP\ Wed\ Apr\ 1\ 20:53:41\ UTC\ 2009\ x86_64\ GNU/Linux\" -DGCC_VER=\"gcc\ Ubuntu\ 4.3.2-1ubuntu12\ 4.3.2\"     -g -O2 -Wall -c seqio.c                                                                                                                                                  
seqio.c: In function ‘seqfgcgify’:                                                                                                                          
seqio.c:2744: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                        
seqio.c:2748: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                        
seqio.c:2750: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                        
seqio.c: In function ‘seqfungcgify’:                                                                                                                        
seqio.c:2968: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                        
seqio.c:3025: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                        
seqio.c: In function ‘putline’:                                                                                                                             
seqio.c:13542: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:13590: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘simple_putseq’:                                                                                                                       
seqio.c:13723: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘genbank_putseq’:                                                                                                                      
seqio.c:13937: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:13952: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:13997: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘pir_putseq’:                                                                                                                          
seqio.c:14151: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14194: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘embl_putseq’:                                                                                                                         
seqio.c:14321: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14337: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14393: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘sprot_putseq’:                                                                                                                        
seqio.c:14536: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14599: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘nbrf_putseq’:                                                                                                                         
seqio.c:14686: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14732: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘nbrfold_putseq’:                                                                                                                      
seqio.c:14797: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14802: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘fasta_putseq’:                                                                                                                        
seqio.c:14839: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:14875: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘fastaold_putseq’:                                                                                                                     
seqio.c:14919: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘stanford_putseq’:                                                                                                                     
seqio.c:14981: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15007: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘stanfordold_putseq’:                                                                                                                  
seqio.c:15052: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15062: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘gcg_putseq’:                                                                                                                          
seqio.c:15118: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘asn_putseq’:                                                                                                                          
seqio.c:15801: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15807: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15811: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15825: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15832: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15839: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15846: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:15953: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘genbank_annotate’:                                                                                                                    
seqio.c:16074: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16114: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16128: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16140: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘pir_annotate’:                                                                                                                        
seqio.c:16179: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16219: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16233: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16245: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘embl_annotate’:                                                                                                                       
seqio.c:16294: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16348: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16362: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16377: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c: In function ‘sprot_annotate’:                                                                                                                      
seqio.c:16425: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16464: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result                                                       
seqio.c:16478: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16490: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c: In function ‘fasta_annotate’:
seqio.c:16519: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16558: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16573: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16585: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c: In function ‘nbrf_annotate’:
seqio.c:16630: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16637: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16677: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16691: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16704: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c: In function ‘stanford_annotate’:
seqio.c:16772: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16786: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16798: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c: In function ‘asn_annotate’:
seqio.c:16907: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16965: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16991: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16992: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:16997: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
seqio.c:17018: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
gcc -DPACKAGE=\"tacg\" -DVERSION=\"4.1.0\" -DHAVE_ST_BLKSIZE=1 -DHAVE_LIBM=1 -DHAVE_LIBPCRE=1 -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_FCNTL_H=1 -DHAVE_UNISTD_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_STRFTIME=1 -DHAVE_VPRINTF=1 -DHAVE_ALLOCA_H=1 -DHAVE_ALLOCA=1 -DHAVE_PUTENV=1 -DHAVE_STRSEP=1 -DHAVE_STRDUP=1 -DHAVE_STRSPN=1 -DHAVE_STRSTR=1 -DHAVE_UNAME=1  -I. -I. -DBUILD_DATE=\"Sun\ Apr\ 12\ 11:16:56\ CEST\ 2009\" -DUNAME=\"Linux\ MartijnDesktop\ 2.6.27-11-generic\ #1\ SMP\ Wed\ Apr\ 1\ 20:53:41\ UTC\ 2009\ x86_64\ GNU/Linux\" -DGCC_VER=\"gcc\ Ubuntu\ 4.3.2-1ubuntu12\ 4.3.2\"     -g -O2 -Wall-c Cutting.c
In file included from Cutting.c:17:
tacg.h:176: error: array type has incomplete element type
tacg.h:178: error: array type has incomplete element type
make: *** [Cutting.o] Error 1
martijn@MartijnDesktop:~/tacg-4.1.0-src$
```

As you can see, the ./CONFIGURE seems to work properly, no giant errors. The make command however, seems to give trouble. It yells about ignoring output from fwrite, and finally it says it has problems with an incomplete element type of an array... suuuure. Then it stops the make file, and if you were to try make install after that it gives basically the same error as when terminating the make.

It's safe to say I'm at a loss as to what I'm doing wrong, but I hoped you all may have any idea?

Kind regards,

Martijn Schmidt.

---

