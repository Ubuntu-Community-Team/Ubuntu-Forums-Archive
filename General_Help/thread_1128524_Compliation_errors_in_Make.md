---
title: "Compliation errors in Make"
date: 2009-04-17
forum: General Help
---

### Post by jrober04 on 2009-04-17
Hello everyone,

I am trying to build 'tophat-0.8.3' and I managed to configure properly.  But the make step fails and I have no clue as to where to even begin troubleshooting it.  Any help would be greatly appreciated.  I am running 64 Ubuntu 8.10 on a core 2 duo.

james@james-desktop:~/Desktop/tophat-0.8.3$ ./configure --prefix=/usr/local/bin/checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gawk... (cached) gawk
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... ar
checking for perl... /usr/bin/perl
checking for bash... /bin/bash
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking if gcc accepts -m64... yes
checking for gzread in -lz... yes
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for int32_t... yes
checking for size_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for memset... yes
checking for strdup... yes
checking for strrchr... yes
checking for strtol... yes
checking for strsep... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

-- TopHat 0.8.3 Configuration Results --
  C compiler:          gcc -Wall -g3 -m64 -O3   -DNDEBUG
  C++ compiler:        g++ -Wall -g3 -m64 -O3   -DNDEBUG
  GCC version:         gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
  Host System type:    x86_64-unknown-linux-gnu
  Install prefix:      /usr/local/bin
  Install eprefix:     ${prefix}

  See config.h for further configuration information.
  Email <cole@cs.umd.edu> with questions and bug reports.

james@james-desktop:~/Desktop/tophat-0.8.3$ make
make  all-recursive
make[1]: Entering directory `/home/james/Desktop/tophat-0.8.3'
Making all in src
make[2]: Entering directory `/home/james/Desktop/tophat-0.8.3/src'
g++ -DHAVE_CONFIG_H -I. -I..    -Wall -g3 -m64 -O3   -DNDEBUG -I./SeqAn-1.1 -Wall -g3 -m64 -O3   -DNDEBUG -MT bwt_map.o -MD -MP -MF .deps/bwt_map.Tpo -c -o bwt_map.o bwt_map.cpp
In file included from ./SeqAn-1.1/seqan/basic.h:54,
                 from ./SeqAn-1.1/seqan/sequence.h:27,
                 from bwt_map.h:14,
                 from bwt_map.cpp:21:
./SeqAn-1.1/seqan/basic/basic_metaprogramming.h:202: error: ‘std::memset’ has not been declared
./SeqAn-1.1/seqan/basic/basic_metaprogramming.h: In static member function ‘static void seqan::MemsetWorker<SIZE, direct>::run(unsigned char*, unsigned char)’:
./SeqAn-1.1/seqan/basic/basic_metaprogramming.h:206: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_metaprogramming.h: In static member function ‘static void seqan::MemsetConstValueWorker<SIZE, direct, c>::run(unsigned char*)’:
./SeqAn-1.1/seqan/basic/basic_metaprogramming.h:252: error: ‘memset’ is not a member of ‘std’
In file included from ./SeqAn-1.1/seqan/basic.h:68,
                 from ./SeqAn-1.1/seqan/sequence.h:27,
                 from bwt_map.h:14,
                 from bwt_map.cpp:21:
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h: In constructor ‘seqan::Allocator<seqan::MultiPool<TParentAllocator, BLOCKING_LIMIT> >::Allocator()’:
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:75: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:76: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:77: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h: In constructor ‘seqan::Allocator<seqan::MultiPool<TParentAllocator, BLOCKING_LIMIT> >::Allocator(TParentAllocator&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:83: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:84: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:85: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h: In copy constructor ‘seqan::Allocator<seqan::MultiPool<TParentAllocator, BLOCKING_LIMIT> >::Allocator(const seqan::Allocator<seqan::MultiPool<TParentAllocator, BLOCKING_LIMIT> >&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:93: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:94: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:95: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h: In function ‘void seqan::clear(seqan::Allocator<seqan::MultiPool<TParentAllocator, BLOCKING_LIMIT> >&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:127: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:128: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_multipool.h:129: error: ‘memset’ is not a member of ‘std’
In file included from ./SeqAn-1.1/seqan/basic.h:69,
                 from ./SeqAn-1.1/seqan/sequence.h:27,
                 from bwt_map.h:14,
                 from bwt_map.cpp:21:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h: In constructor ‘seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >::Allocator()’:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h:83: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h: In constructor ‘seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >::Allocator(size_t)’:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h:91: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h: In constructor ‘seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >::Allocator(TParentAllocator&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h:102: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h: In constructor ‘seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >::Allocator(size_t, TParentAllocator&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h:112: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h: In copy constructor ‘seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >::Allocator(const seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h:125: error: ‘memset’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h: In function ‘void seqan::clear(seqan::Allocator<seqan::ChunkPool<SIZE, MAX_COUNT, TParentAllocator> >&)’:
./SeqAn-1.1/seqan/basic/basic_allocator_chunkpool.h:159: error: ‘memset’ is not a member of ‘std’
In file included from ./SeqAn-1.1/seqan/basic.h:101,
                 from ./SeqAn-1.1/seqan/sequence.h:27,
                 from bwt_map.h:14,
                 from bwt_map.cpp:21:
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h: In function ‘void seqan::_arrayCopyForward_Pointer(TValue*, TValue*, TValue*, seqan::True)’:
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h:207: error: ‘memmove’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h: In function ‘void seqan::_arrayCopyBackward_Pointer(TValue*, TValue*, TValue*, seqan::True)’:
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h:241: error: ‘memmove’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h: In function ‘void seqan::_arrayMoveForward_Pointer(TValue*, TValue*, TValue*, seqan::True)’:
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h:275: error: ‘memmove’ is not a member of ‘std’
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h: In function ‘void seqan::_arrayMoveBackward_Pointer(TValue*, TValue*, TValue*, seqan::True)’:
./SeqAn-1.1/seqan/basic/basic_alphabet_trait_basic.h:309: error: ‘memmove’ is not a member of ‘std’
In file included from ./SeqAn-1.1/seqan/sequence.h:52,
                 from bwt_map.h:14,
                 from bwt_map.cpp:21:
./SeqAn-1.1/seqan/sequence/string_pointer.h: In function ‘size_t seqan::length(char*)’:
./SeqAn-1.1/seqan/sequence/string_pointer.h:336: error: ‘strlen’ is not a member of ‘std’
./SeqAn-1.1/seqan/sequence/string_pointer.h: In function ‘size_t seqan::length(const char*)’:
./SeqAn-1.1/seqan/sequence/string_pointer.h:343: error: ‘strlen’ is not a member of ‘std’
In file included from ./SeqAn-1.1/seqan/sequence.h:62,
                 from bwt_map.h:14,
                 from bwt_map.cpp:21:
./SeqAn-1.1/seqan/sequence/sequence_multiple.h: In function ‘typename seqan::Size<seqan::String<TValue, TSpec> >::Type seqan::_findIthNonZeroValue(const seqan::String<TValue, TSpec>&, TPos)’:
./SeqAn-1.1/seqan/sequence/sequence_multiple.h:995: warning: suggest explicit braces to avoid ambiguous ‘else’
bwt_map.cpp: In member function ‘virtual bool SplicedBowtieHitFactory::get_hit_from_buf(const char*, BowtieHit&, bool, char*, char*)’:
bwt_map.cpp:298: warning: comparison between signed and unsigned integer expressions
make[2]: *** [bwt_map.o] Error 1
make[2]: Leaving directory `/home/james/Desktop/tophat-0.8.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/Desktop/tophat-0.8.3'
make: *** [all] Error 2

---

