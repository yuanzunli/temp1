kdeLF
=====

**kdeLF** is an MIT licensed Python-Fortran implementation of Yuan et al (2020)'s
`Luminosity function estimator via Kernel density estimation
<https://ui.adsabs.harvard.edu/abs/2020ApJS..248....1Y/abstract>`_ and these pages will
show you how to use it.

This documentation won't teach you too much about Kernel density estimation (KDE) but there are a lot
of resources available for that (try `this one
<https://www.inference.org.uk/mackay/itprnn/book.html>`_).
We also `published a paper <https://arxiv.org/abs/1202.3665>`_ explaining
the KDE algorithm and implementation in detail.

kdeLF has been used in :doc:`quite a few projects in the astrophysical literature
<testimonials>` and it is being actively developed on `GitHub
<https://github.com/yuanzunli/kdeLF>`_.

.. image:: https://img.shields.io/badge/GitHub-dfm%2Femcee-blue.svg?style=flat
    :target: https://github.com/yuanzunli/kdeLF
.. image:: https://github.com/dfm/emcee/workflows/Tests/badge.svg
    :target: https://github.com/dfm/emcee/actions?query=workflow%3ATests
.. image:: https://img.shields.io/badge/license-MIT-blue.svg?style=flat
    :target: https://github.com/dfm/emcee/blob/master/LICENSE
.. image:: https://img.shields.io/badge/arXiv-1202.3665-orange.svg?style=flat
    :target: https://arxiv.org/abs/1202.3665
.. image:: https://coveralls.io/repos/github/dfm/emcee/badge.svg?branch=master&style=flat
    :target: https://coveralls.io/github/dfm/emcee?branch=master


Basic Usage
-----------

If you wanted to draw samples from a 5 dimensional Gaussian, you would do
something like:

.. code-block:: python

    import numpy as np
    import emcee

    def log_prob(x, ivar):
        return -0.5 * np.sum(ivar * x ** 2)

    ndim, nwalkers = 5, 100
    ivar = 1. / np.random.rand(ndim)
    p0 = np.random.randn(nwalkers, ndim)

    sampler = emcee.EnsembleSampler(nwalkers, ndim, log_prob, args=[ivar])
    sampler.run_mcmc(p0, 10000)

A more complete example is available in the :ref:`quickstart` tutorial.


How to Use This Guide
---------------------

To start, you're probably going to need to follow the :ref:`install` guide to
get kdeLF installed on your computer.
After you finish that, you can probably learn most of what you need from the
tutorials listed below (you might want to start with
:ref:`quickstart` and go from there).
If you need more details about specific functionality, the User Guide below
should have what you need.

We welcome bug reports, patches, feature requests, and other comments via `the GitHub
issue tracker <https://github.com/yuanzunli/kdeLF/issues>`_, but you should check out the
`contribution guidelines <https://github.com/yuanzunli>`_
first.
If you have a question about the use of kdeLF, please feel free to contact the Author. 


.. toctree::
   :maxdepth: 2
   :caption: User Guide

   user/install
   user/sampler
   user/moves
   user/blobs
   user/backends
   user/autocorr
   user/upgrade
   user/faq



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

