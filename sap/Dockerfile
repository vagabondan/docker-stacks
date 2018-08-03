# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
FROM jupyter/tensorflow-notebook

LABEL maintainer="Vagabondan <strannix.vagabondan@gmail.com>"

USER root

RUN apt-get update -y && \
    apt-get install -y cmake && \
    apt-get install -y make && \
    apt-get -y install libboost-all-dev

RUN cd /home/$NB_USER && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER && \
    fix-permissions /home/$NB_USER/.cache

USER $NB_UID


# Install Tensorflow
RUN pip install --upgrade pip && \
    pip install \
    xgboost \
    lightgbm \
    LCfeatures \
    wordbatch \
    hdbscan \
    graphviz \
    pydotplus \
    IPython \
    Treeinterpreter \
    LIME \
    ELI5 \
    pyhdb \
    protobuf \
    tqdm \
    wheel

RUN conda install gxx_linux-64 && \
    pip install keras
#    pip install -U --no-deps --force-reinstall --install-option="--rl=True" skater==1.1.1b2

RUN git clone --branch=stable https://github.com/bigartm/bigartm.git && \
    cd bigartm && \
    mkdir build && cd build && \
    cmake .. && \
    make -j4 && \
    cd /home/$NB_USER && \
    git clone https://github.com/sato9hara/defragTrees.git

RUN git clone https://github.com/SAP/PyHDB.git && \
    cd PyHDB && \
    python setup.py install && \
    cd ..


# RUN ln -s BayesianOptimization BayesianOptimization-master && \
#    git clone https://github.com/IBCNServices/GENESIM.git && \
#    cd GENESIM && \
#    ./install.sh && \
#    cd /home/$NB_USER

# RUN fix-permissions /home/$NB_USER    

# USER $NB_UID
