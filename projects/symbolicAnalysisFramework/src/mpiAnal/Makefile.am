include $(top_srcdir)/config/Makefile.for.ROSE.includes.and.libs
include $(top_srcdir)/projects/symbolicAnalysisFramework/common.for.dep.libs

# Saf is the short for symbolic analysis framework.
# it is used to avoid possible name collision 
# strange error for corrupted mesgExpr.lo, disabling parallel build for this target
.NOTPARALLEL:libSafmpiAnal.la 
noinst_LTLIBRARIES = libSafmpiAnal.la
libSafmpiAnal_la_SOURCES = \
                   mesgExpr.C \
                   rankDepAnalysis.C \
                   contProcMatchAnalysis.C  \
                   mesgBuf.C \
                   pCFG.C \
		   procSet.C \
                   ranknpDepIfMeet.C

include_HEADERS = contProcMatchAnalysis.h  mesgBuf.h  mesgExpr.h  pCFG.h procSet.h  rankDepAnalysis.h  ranknpDepIfMeet.h
# ----------test program -------------------
#.NOTPARALLEL: commTopoAnalTest  selfTest 
noinst_PROGRAMS = commTopoAnalTest  selfTest
selfTest_SOURCES = selfTest.C
commTopoAnalTest_SOURCES = commTopoAnalTest.C
LDADD = $(LIBS_WITH_RPATH) $(ROSE_LIBS) \
         $(SAF_BUILD_ROOT)/src/mpiAnal/libSafmpiAnal.la  \
         $(SAF_BUILD_ROOT)/src/external/libSafexternal.la

# Liao 10/12/2010, this test fails on our boost version test for 1.39.0 , 1.42.0 and 1.43.0
check-local:selfTest
#	./selfTest $(srcdir)/test_example.c

EXTRA_DIST =  fanExchange.C fanoutBcast.C fanInGather.C pCFG_Partitioned.C
clean-local:
	rm -rf *.o rose_*.[cC] *.dot *.out rose_*.cpp *.patch *.loT  detail.html summary.html index.html dbg_imgs


