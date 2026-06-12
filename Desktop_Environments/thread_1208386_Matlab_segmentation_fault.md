---
title: "Matlab segmentation fault"
date: 2009-07-09
forum: Desktop Environments
---

### Post by ythaaa on 2009-07-09
Hi 

i have installed matlab on kubuntu successfully (i hope) but could not start up..... starting matlab will cause the application to not responding. starting with matlab -nojvm also gives me problem as shown in attached file.

can anyone help me with this? 

thanks you very much in advance

---

### Post by ythaaa on 2009-07-09
------------------------------------------------------------------------
       Segmentation violation detected at Thu Jul  9 17:36:38 2009
------------------------------------------------------------------------

Configuration:
  MATLAB Version:   7.0.0.19901 (R14)
  Operating System: Linux 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
  Window System:    The X.Org Foundation (10600000), display :0.0
  Current Visual:   0x21 (class 4, depth 24)
  Processor ID:     x86 Family 6 Model 14 Stepping 8, GenuineIntel
  Virtual Machine:  Java is not enabled
  Default Charset:  UTF-8

Register State:
  eax = 00000090   ebx = b802cff4
  ecx = 00000000   edx = 00000000
  esi = 00000006   edi = b49093ec
  ebp = bf826ba8   esp = bf826a30
  eip = b801adda   flg = 00010246

Stack Trace:
  [0] ld-linux.so.2:0xb801adda(0x0908a5d8, 0x0908ad10, 0, 0)
  [1] ld-linux.so.2:0xb802235b(0xbf826d1c, 0, 0, 0)
  [2] ld-linux.so.2:0xb801e036(0xb80220d0, 0xbf826d1c, 0xb7f8dc97 "v7.0", 0xb7d3e5cb "v7.0")
  [3] ld-linux.so.2:0xb8021c1e(0x0955cfb6 "/usr/share/Matlab/bin/glnx86/lib..", 0x80000002, 0xb7f9775c, 0xfffffffe)
  [4] libdl.so.2:0xb76b3bec(0xbf826eb0, 0, 0xb802cff4, 0x7d0ef6a3)
  [5] ld-linux.so.2:0xb801e036(0xb76b3b50, 0xbf826eb0, 0xb76b3b50, 0xb76b5ff4 ")
  [6] libdl.so.2:0xb76b401c(0xbf826ee0, 0xb801de7b, 0xb7dbc498, 0xb649aa68)
  [7] libdl.so.2:dlopen~(0x0955cfb6 "/usr/share/Matlab/bin/glnx86/lib..", 2, 0xb7d99e68, 0xb4ae6d10) + 65 bytes
  [8] libut.so:utLoadLibrary(0x0955cfb6 "/usr/share/Matlab/bin/glnx86/lib..", 0xbf826f2c, 0x4d2f6572, 0xb7d51482) + 40 bytes
  [9] libmwm_dispatcher.so:Mlm_builtin::load_mf()(0xb4ae6d10, 0xb7da9a74, 0xb4ae6d10, 0xb7d498e6) + 666 bytes
  [10] libmwm_dispatcher.so:Mlm_MATLAB_fn::try_load()(0xb4ae6d10, 0xbf826fec, 0xbf826fe8, 0xb797aff4) + 46 bytes
  [11] libmwm_dispatcher.so:Mdispatcher::add_file(int, char const*, Mlm_file*&, Mfh_file*&, bool)(0x09549080, 0, 0x0955d192 "/usr/share/Matlab/toolbox/local/..", 0xbf8280a4) + 268 bytes
  [12] libmwm_dispatcher.so:Mdispatcher::fill_vectors(mpPath_tag*, int, std::vector<char const*, std::allocator<char const*> > const&, std::vector<Mfh_MATLAB_fn*, std::allocator<Mfh_MATLAB_fn*> >&, std::vector<char const*, std::allocator<char const*> >&, bool, bool, bool, bool)(0x09549080, 1, 450, 0x0954a2ac) + 991 bytes
  [13] libmwm_dispatcher.so:Mdispatcher::rebuild(int, bool)(0x09549080, 450, 0, 0xb7d31918 "_ZN11Mdispatcher8lookup_TI19Mtyp..") + 221 bytes
  [14] libmwm_dispatcher.so:Mfh_rebuild::lookup(int, Mtypeidx_attributes**)(0xb4aec2ac, 1, 0xbf828288, 0x0954cbe4) + 35 bytes
  [15] libmwm_dispatcher.so:Mfunction_handle* Mdispatcher::lookup_T<Mtypeidx_attributes>(Mfh_MATLAB_fn*, int, int, Mtypeidx_attributes**)(0x09549080, 0, 450, 1) + 188 bytes
  [16] libmwm_dispatcher.so:mdGlobalFunctionBinding::lookup(int, Mtypeidx_attributes**)(0xb4972cd0, 1, 0xbf828288, 0xb7d65e0a) + 41 bytes
  [17] libmwm_dispatcher.so:Mdispatcher::get_binding(Mfh_MATLAB_fn*, int)(0x09549080, 0, 450, 0xb7d8245a) + 249 bytes
  [18] libmwm_dispatcher.so:mdGetFcnIndex_helper(Mdispatcher*, Mfh_MATLAB_fn*, char const*, bool)(0x09549080, 0, 0x09012871 "matlabrc", 0) + 77 bytes
  [19] libmwm_interpreter.so:in_is_matlab_function(0x090cce70 ", 0xbf828ef8 ", 0x09012871 "matlabrc", 3) + 109 bytes
  [20] libmwm_parser.so:mps_look_up_categorized_identifier(0x090cf6e4, 0xbf8283e0, 0xb53f4f54, 0xb7ffa444) + 738 bytes
  [21] libmwm_parser.so:mps_convert_M_ID(0x090cf6e4, 0xb53f4f50, 28672, 0xb7453866) + 614 bytes
  [22] libmwm_parser.so:mps_convert(0x090cf6e4, 0xb53f4f50, 0, 0xb6fd9480) + 141 bytes
  [23] libmwm_parser.so:mps_convert_M_Stmt_2(0x090cf6e4, 0xb53f4f94, 0xbf828508, 0xb744f4de) + 177 bytes
  [24] libmwm_parser.so:mps_convert_M_Stmts_2(0x090cf6e4, 0xb53f4fb0, 0xbf8285c4, 0xb54fab50) + 999 bytes
  [25] libmwm_parser.so:mps_make_M_body_from_parse_tree(0x090cf6e4, 0xb53f4fb0, 0, 8) + 787 bytes
  [26] libmwm_parser.so:mps_convert_script(0x090cf6e4, 0xb53f4fb0, 0x090ce790, 0) + 1236 bytes
  [27] libmwm_parser.so:mps_M_to_IR_eval_with_pragmas(0xbf828be8, 0xbf828ab0, 0xbf828ab4, 0xbf828ab8) + 2042 bytes
  [28] libmwm_parser.so:mps_text_to_IR(0xbf828b63, 0xbf828be8, 0xbf828ab0, 0xbf828ab4) + 409 bytes
  [29] libmwm_parser.so:mps_string_to_IR(0xbf828b63, 0xbf828be8, 0, 0) + 228 bytes
  [30] libmwm_parser.so:mps_statement_to_IR_with_visible_names(0xbf828be8, 0, 0x090cf6e4, 0xb7e539e0 "matlabrc") + 80 bytes
  [31] libmwm_interpreter.so:in_parse_and_create_pcode(0xb7ffa444, 0xbf828ee0, 0xbf828c98, 0) + 321 bytes
  [32] libut.so:ut_try_catch_id(0xb7ffa444, 0xbf828ee0, 0xb7af2568, 0xb7af289c) + 115 bytes
  [33] libmwm_interpreter.so:inEvalStringWithIsVarFcn(_memory_context*, char const*, unsigned, EvalType, int, mxArray_tag**, inDebugCheck, _pcodeheader*, int*, bool (*)(void*, char const*), void*)(0xb7ffa464, 0xb7e539e0 "matlabrc", 8, 0) + 1598 bytes
  [34] libmwm_interpreter.so:inEvalCmdWithLocalReturn(0xb7e539e0 "matlabrc", 0, 0xb7ff00a4, 0xb7af0c72) + 111 bytes
  [35] libmwm_interpreter.so:inEvalCmd(0xb7e539e0 "matlabrc", 0xb7e5cb08, 0xbf82a988, 0xb7df7801) + 30 bytes
  [36] libmwbridge.so:mnRunLoginScript(0xb7dd2774, 0x09549080, 0xbf82aa78, 0xb7dc9993) + 162 bytes
  [37] libmwbridge.so:mnRunPathDependentInitialization()(0xb7eb4de0, 0x0804a68c, 0xbf82aa04, 0x09549080) + 37 bytes
  [38] libmwmcr.so:mcr_init_handler_cpp(mcrInstance*, mcrOptionsInternal*, MfileReader*, bool volatile*, bool volatile*)(0x0901d090, 0x0901b070, 0x0901d0b8, 0xbf82aaaf) + 531 bytes
  [39] libmwmcr.so:mcrInstance::mcrInstance(mcrOptions&, MfileReader*)(0x0901d090, 0xbf82ad40, 0x0901d0b8, 0) + 481 bytes
  [40] MATLAB:mcrMain(int, char**)(2, 0xbf82ce34, 0xbf82cda8, 0xb784ae30) + 239 bytes
  [41] MATLAB:main(2, 0xbf82ce34, 0xbf82ce40, 0xb649a238) + 23 bytes
  [42] libc.so.6:__libc_start_main~(0x0804a7d0, 2, 0xbf82ce34, 0x0804a3e4) + 229 bytes

Please follow these steps in reporting this problem to The MathWorks so
that we have the best chance of correcting it:

  1. Send this crash report to [email]segv@mathworks.com[/email] for automated analysis.
     For your convenience, this information has been recorded in:
       /home/yth/matlab_crash_dump.3645

  2. Also, if the problem is reproducible, send the crash report to
     [email]support@mathworks.com[/email] along with:
       - A specific list of steps that will reproduce the problem
       - Any M, MEX, MDL or other files required to reproduce the problem
       - Any error messages displayed to the command window
     A technical support engineer will contact you with further information.

Thank you for your assistance.  Please save your workspace and restart
MATLAB before continuing your work.

---

### Post by Villiam on 2009-07-09
The problem could be with  java. Try running matlab -n There is path for MATLAB_JAVA?.
Try establishing the path with:

$  export MATLAB_JAVA=3D/usr/lib/jvm/java-6-sun-[1.6.0.07/jre/bin/java]("http://1.6.0.07/jre/bin/java") ; matlab/bin/matlab

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by ythaaa on 2009-07-11
hey thanks a lot.... it solve my problem!!!!! thanks thanks thanks thanks thanks thanks 

btw... i realize when i restart, the link is gone again. how do i premanently add in the entry?? thanks again!!!!

---

