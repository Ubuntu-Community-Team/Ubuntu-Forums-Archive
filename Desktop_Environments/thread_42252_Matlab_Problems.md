---
title: "Matlab Problems"
date: 2005-06-16
forum: Desktop Environments
---

### Post by abhia7 on 2005-06-16
I am trying to run Matlab R14-SP1 on Hoary. 
The problem I am facing is that I cannot run Simulink. Matlab installation proceeds without a flaw, but as soon as I start Simulink, Matlab crashes, and I get the following error: 

simulink
??? Can't load '/usr/local/matlab7/bin/glnx86/libmwsimulink.so': libXft.so.1: cannot open shared object file: No such file or directory

??? Insufficient memory to execute script %.


------------------------------------------------------------------------
             Assertion detected at Thu Jun 16 16:43:56 2005
------------------------------------------------------------------------

Assertion failed: hdr->in_use != 0, at line 706 of file "memmgr/memcache.cpp".
Attempt to free previously freed memory


Did anyone face a similar problem?

---

### Post by emmet on 2005-06-29
Hi,

Have you seen anything on the Matlab website? This might not be a strictly Ubuntu problem. 

Emmet

---

### Post by JPLGuy on 2006-12-09
A specifically Ubuntu solution is to use Synaptic to install the package libxft1. This solved the "libXft.so.1: cannot open shared object file: No such file or directory" problem for me under Ubuntu 6.10. It did make the fonts in Simulink's menu horribly ugly, but at least it works!

I gather that the problem is libXft.so.1 is an outdated version of the X fonts, more recent packages are available, but the older MATLAB versions like 7.0.1 (R14) are set to use the older version. Let's hope that this package is maintained for the forseeable future!

---

### Post by ametade on 2006-12-15
Hi there,

I managed to solve the problem with the "libXft.so.1" error message, but now when I try to start Similink, Matlab crashes. I get the following crash dump:
```

  [0] libmwm_interpreter.so:inInAMexFile(0xb5338790 "Stateflow Internal Warning: Jump..", 0xbff41ac0 "Stateflow Internal Warning: Jump..", 1, 0xa5bbfeb0 ") + 37 bytes
  [1] libmwm_interpreter.so:inWarningCallbackFcn()(0xa5bbfeb0 ", 0xb7e65960, 0xbff433e8, 0xb7e604cf) + 113 bytes
  [2] libut.so:utCallRegisteredWarningCallback(0xa5bbfeb0 ", 0xb75c3fb1, 0xbff41ac0 "Stateflow Internal Warning: Jump..", 0xbff43418) + 26 bytes
  [3] libmx.so:mxFormatAndIssueWarning(bool, char const*, char const*, char*)(0, 0xb75c3fb1, 0xb75c3fa0 "%s", 0xbff43418) + 435 bytes
  [4] libmx.so:mxWarningMsgIdAndTxt(0xb75c3fb1, 0xb75c3fa0 "%s", 0xbff43440 "Stateflow Internal Warning: Jump..", 0xbff43c54) + 23 bytes
  [5] libmex.so:mexWarnMsgTxt@libmex.INTERNAL(0xbff43440 "Stateflow Internal Warning: Jump..", 2048, 0xa37869c0 "Stateflow Internal Warning: Jump..", 0xbff43c54) + 50 bytes
  [6] sf.mexglx:mex_warn_message(0xa37869c0 "Stateflow Internal Warning: Jump..", 1, 2, 0xb7e6e114) + 55 bytes
  [7] sf.mexglx:safe_mex_call_matlab(0, 0xbff43e0c, 2, 0xbff43ca0) + 121 bytes
  [8] sf.mexglx:private_safe_mex_call_matlab(0, 0xbff43e0c, 0, 0) + 124 bytes
  [9] sf.mexglx:try_mexFunction(1, 0xbff446dc, 3, 0xbff446e0) + 217 bytes
  [10] sf.mexglx:mexFunction(1, 0xbff446dc, 3, 0xbff446e0) + 74 bytes
  [11] libmex.so:mexRunMexFile(1, 0xbff446dc, 3, 0xbff446e0) + 93 bytes
  [12] libmex.so:Mfh_mex::dispatch_file(int, mxArray_tag**, int, mxArray_tag**)(0xb5434e40, 1, 0xbff446dc, 3) + 537 bytes
  [13] libmwm_dispatcher.so:Mfh_file::dispatch_fh(int, mxArray_tag**, int, mxArray_tag**)(0xb5434e40, 1, 0xbff446dc, 3) + 270 bytes
  [14] libmwm_interpreter.so:inCallFcnWithTrap(1, 0xbff446dc, 3, 0xbff446e0) + 259 bytes
  [15] libmwsimulink.so:slCallFcnWithTrapping(1, 0xbff446dc, 3, 0xbff446e0) + 75 bytes
  [16] libmwsimulink.so:callSlSfCommand(slBlockDiagram_tag*, double, char const*)(0x08c0a6a0, 0, 0xbff00000, 0xa51dd0c4 "mdlLoad") + 186 bytes
  [17] libmwsimulink.so:slNotifyStateflowModelEvent(slBlockDiagram_tag*, SL_Event_Type)(0x08c0a6a0, 0, 0, 0xa4de5f99) + 89 bytes
  [18] libmwsimulink.so:sl_LoadBlockDiagramIncrementally(0, 0xbff44a90 "/opt/matlab/toolbox/simulink/blo..", 0, 0) + 1457 bytes
  [19] libmwsimulink.so:sl_LoadBlockDiagramModel(0xbff44a90 "/opt/matlab/toolbox/simulink/blo..", 0, 0, 0) + 199 bytes
  [20] libmwsimulink.so:sluLoadModel(char const*, bool, slBlockDiagram_tag**)(0x08c09584 "/opt/matlab/toolbox/simulink/blo..", 1, 0xbff45bdc, 1) + 272 bytes
  [21] libmwsimulink.so:matl_open_system(int, mxArray_tag**, int, mxArray_tag**)(0, 0xbff45c34, 1, 0xbff45c38 ") + 385 bytes
  [22] libmwsimulink.so:slLaunchSimulink(int, mxArray_tag**, int, mxArray_tag**)(0, 0xbff45f70, 0, 0xbff45fd0) + 105 bytes
  [23] libmwm_dispatcher.so:Mfh_builtin<mxArray_tag>::dispatch_mf(int, mxArray_tag**, int, mxArray_tag**)(0xb542d3a0, 0, 0xbff45f70, 0) + 53 bytes
  [24] libmwm_dispatcher.so:Mfh_MATLAB_fn::dispatch_fh(int, mxArray_tag**, int, mxArray_tag**)(0xb542d3a0, 0, 0xbff45f70, 0) + 196 bytes
  [25] libmwm_interpreter.so:inDispatchFromStack(439, 0xb5430ec4 "simulink", 0, 0) + 503 bytes
  [26] libmwm_interpreter.so:inDispatchCall(char const*, int, int, int, int*, int*)(0xb5430ec4 "simulink", 439, 0, 0) + 145 bytes
  [27] libmwm_interpreter.so:.L522(2, 0, 0, 0) + 141 bytes
  [28] libmwm_interpreter.so:inInterPcodeSJ(inDebugCheck, int, int, opcodes, inPcodeNest_tag*)(2, 0, 0, 0) + 300 bytes
  [29] libmwm_interpreter.so:inInterPcode(2, 0, 0xbff464e8, 0xb79ec317) + 54 bytes
  [30] libmwm_interpreter.so:in_local_call_eval_function(int*, _pcodeheader*, int*, mxArray_tag**, inDebugCheck)(0, 0xbff46ee0, 0xbff46f70, 0xbff46fa8) + 163 bytes
  [31] libmwm_interpreter.so:inEvalStringWithIsVarFcn(_memory_context*, char const*, unsigned, EvalType, int, mxArray_tag**, inDebugCheck, _pcodeheader*, int*, bool (*)(void*, char const*), void*)(0xb7ef4464, 0x0861d5b0 "simulink\n", 9, 0) + 2358 bytes
  [32] libmwm_interpreter.so:inEvalCmdNoEnd(0x0861d5b0 "simulink\n", 0x0861d5b0 "simulink\n", 0xbff47158, 0xb7cf2dc3) + 110 bytes
  [33] libmwbridge.so:mnParser(0xb7cc8e8b "@@@", 0xb7cc8f7b "mnParser", 1, 0x01f47210) + 471 bytes
  [34] libmwmcr.so:mcrInstance::mnParser()(0x0809e480, 0, 0xbff49498, 0x0804a90e) + 96 bytes
  [35] MATLAB:mcrMain(int, char**)(1, 0xbff49544, 0xbff494b8, 0xb7785470) + 308 bytes
  [36] MATLAB:main(1, 0xbff49544, 0xbff4954c, 0xb7f23878 ") + 23 bytes
  [37] libc.so.6:__libc_start_main~(0x0804a7d0, 1, 0xbff49544, 0x0804a3e4) + 220 bytes

```

Any idea how to solve this problem?

---

### Post by ametade on 2006-12-16
I managed to open simulink without crashing matlab. I started matlab with the -nojmv option:
```
matlab -nojvm
```

---

