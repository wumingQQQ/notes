 **完整的Rag应用的检索增强环节**

> 来源：https://github.com/langchain4j/langchain4j-examples/tree/main/rag-examples/src/main/java/_3_advanced



1. 重写查询：根据历史会话与当前用户查询重写查询，提高后续检索质量

   ~~~txt
   // main class
   QueryTransformer
   ContentRetriever		// 专门负责内容检索
   RetrievalAugmentor		// pipeline，对用户输入进行增强，是rag流程的编排器
   ~~~

2. 查询路由：如果存在多个数据源，可以在检索时定义查询路由

   ~~~txt
   QueryRouter		// 接口
   ContentRetriever
   RetrievalAugmentor
   ~~~

3. 重排序：对检索到的文档重排序，选取最相关的文档

   ~~~txt
   ScoringModel
   ContentAggregator
   ContentRetriever
   RetrievalAugmentor
   ~~~

4. 检索数据注入：可以指示怎样将检索到的文档注入提示词

   ~~~txt
   ContentInjector		// 接口，默认实现DefaultContentInjector
   ContentRetriever
   RetrievalAugmentor
   ~~~

5. 元信息过滤：检索时对文档的元信息做出要求

   ~~~txt
   Filter
   ContentRetriever
   ~~~

6. 跳过检索：某些时候用户输入的query与知识库无关，此时无须检索

   ~~~txt
   QueryRouter		// 自定义实现类实现路由逻辑，当无须检索时返回空列表
   ~~~

7. 联网搜索

   ~~~txt
   WebSearchEngine
   WebSearchContentRetriever
   ~~~

   

