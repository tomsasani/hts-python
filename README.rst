hts-python
==========

pythonic wrapper for [htslib](https://github.com/samtools/htslib.git) C-API using python [cffi](https://cffi.readthedocs.org/).

There is enough functionality for this to be useful, but it still needs a lot of work.
[![Documentation Status](https://readthedocs.org/projects/hts-python/badge/?version=latest)](http://hts-python.readthedocs.io/en/latest/?badge=latest)
[![Build Status](https://travis-ci.org/quinlan-lab/hts-python.svg?branch=master)](https://travis-ci.org/quinlan-lab/hts-python)
[![codecov](https://codecov.io/gh/quinlan-lab/hts-python/branch/master/graph/badge.svg)](https://codecov.io/gh/quinlan-lab/hts-python)

Installation
------------

1. Install `htslib <https://github.com/samtools/htslib.git>`_ using :: 
    make install
2. Then, :: 
    pip/easy_install python `cffi <https://cffi.readthedocs.org/>`_.
3. Finally, :: 
    python setup.py install (--user) 
   from this directory.

Development
-----------

This is a work in progress that relies on the hts library. All of the wrapped functions are included in `hts/hts_concat.h` and then available from python as, e.g. `htslib.sam_read1`

When C-functions not provided by the api are needed, they are added to `hts_extra.c/.h`.

One can run the tests with: `python -c "import hts; hts.doctests()"`

There is enough functionality for this to be quite useful but most of it
is limited to getters, not setters, to, for example update an INFO field
or modify the bam quality scores.

Things to work on:

1. Make properties settable in hts.bam. 
   Currently, they are read-only properties. At very least, it will be useful
   to have setters for seq, base_q, qname, tname, pos, strand, flag.

2. Wrap B/VCF stuff? (in progress)


Why
---

Why use this when `pysam` exists? It's an experiment with python cffi and to provide a pythonic access to htslib.
