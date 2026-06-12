---
title: "Failure :- sudo perl -MCPAN -e 'install XML::Simple'"
date: 2005-11-08
forum: Desktop Environments
---

### Post by poison on 2005-11-08
Hi

I get the following issues when tring to run sudo perl -MCPAN -e 'install XML::Simple' on my Ubuntu 5.10 can someone help please ?

PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    Not Installed
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 1/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 188/196Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 1/38Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255


Thanks

---

### Post by bugardifieno on 2006-07-20
There are a couple of suggestions elsewhere in the forums here: [http://www.ubuntuforums.org/showthread.php?p=1278352#post1278352:](http://www.ubuntuforums.org/showthread.php?p=1278352#post1278352:)) :)

---

