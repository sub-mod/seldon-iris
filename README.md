## seldon-iris

```
s2i build -E environment_rest . seldonio/seldon-core-s2i-python3:0.18 sub_mod/sklearn-iris:0.1
```

```
docker run -it --rm -p 5000:5000 sub_mod/sklearn-iris:0.1
starting microservice
2021-04-12 19:40:55,023 - seldon_core.microservice:main:190 - INFO:  Starting microservice.py:main
2021-04-12 19:40:55,026 - seldon_core.microservice:main:246 - INFO:  Parse JAEGER_EXTRA_TAGS []
2021-04-12 19:40:55,026 - seldon_core.microservice:main:257 - INFO:  Annotations: {}
2021-04-12 19:40:55,026 - seldon_core.microservice:main:261 - INFO:  Importing IrisClassifier
/opt/conda/lib/python3.7/site-packages/sklearn/base.py:315: UserWarning: Trying to unpickle estimator LogisticRegression from version 0.23.2 when using version 0.24.1. This might lead to breaking code or invalid results. Use at your own risk.
  UserWarning)
/opt/conda/lib/python3.7/site-packages/sklearn/base.py:315: UserWarning: Trying to unpickle estimator Pipeline from version 0.23.2 when using version 0.24.1. This might lead to breaking code or invalid results. Use at your own risk.
  UserWarning)
2021-04-12 19:40:55,270 - seldon_core.microservice:main:325 - INFO:  REST microservice running on port 5000
2021-04-12 19:40:55,270 - seldon_core.microservice:main:369 - INFO:  Starting servers
 * Serving Flask app "seldon_core.wrapper" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
2021-04-12 19:40:55,285 - werkzeug:_log:113 - INFO:   * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
2021-04-12 19:41:06,258 - seldon_core.user_model:client_class_names:166 - INFO:  class_names is not implemented
2021-04-12 19:41:06,258 - seldon_core.user_model:client_custom_tags:134 - INFO:  custom_tags is not implemented
2021-04-12 19:41:06,259 - seldon_core.user_model:client_custom_tags:134 - INFO:  custom_tags is not implemented
2021-04-12 19:41:06,259 - seldon_core.user_model:client_custom_metrics:307 - INFO:  custom_metrics is not implemented
2021-04-12 19:41:06,260 - werkzeug:_log:113 - INFO:  172.17.0.1 - - [12/Apr/2021 19:41:06] "POST /predict HTTP/1.1" 200 -
^C%
```

```
curl  -s http://localhost:5000/predict -H "Content-Type: application/json" -d '{"data":{"ndarray":[[5.964,4.006,2.081,1.031]]}}'
{"data":{"names":["t:0","t:1","t:2"],"ndarray":[[0.893123090056503,0.10687335549522325,3.5544482737072013e-06]]},"meta":{}}
```