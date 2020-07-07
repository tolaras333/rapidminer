<?xml version="1.0" encoding="UTF-8"?><process version="8.0.001">
  <context>
    <input/>
    <output/>
    <macros/>
  </context>
  <operator activated="true" class="process" compatibility="8.0.001" expanded="true" name="Process">
    <parameter key="logverbosity" value="init"/>
    <parameter key="random_seed" value="2001"/>
    <parameter key="send_mail" value="never"/>
    <parameter key="notification_email" value=""/>
    <parameter key="process_duration_for_mail" value="30"/>
    <parameter key="encoding" value="SYSTEM"/>
    <process expanded="true">
      <operator activated="true" class="social_media:search_twitter" compatibility="7.3.000" expanded="true" height="68" name="$GE" width="90" x="179" y="901">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query" value="$GE"/>
        <parameter key="result_type" value="recent or popular"/>
        <parameter key="limit" value="100"/>
        <parameter key="language" value="en"/>
        <parameter key="until" value="2018.02.04 16:29:29 -0600"/>
        <parameter key="filter_by_geo_location" value="false"/>
        <parameter key="radius_unit" value="miles"/>
      </operator>
      <operator activated="true" class="social_media:search_twitter" compatibility="7.3.000" expanded="true" height="68" name="$IBM" width="90" x="179" y="1003">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query" value="$IBM"/>
        <parameter key="result_type" value="recent or popular"/>
        <parameter key="limit" value="100"/>
        <parameter key="language" value="en"/>
        <parameter key="until" value="2018.02.04 16:29:29 -0600"/>
        <parameter key="filter_by_geo_location" value="false"/>
        <parameter key="radius_unit" value="miles"/>
      </operator>
      <operator activated="true" class="social_media:search_twitter" compatibility="7.3.000" expanded="true" height="68" name="$AMZN" width="90" x="179" y="1105">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query" value="$AMZN"/>
        <parameter key="result_type" value="recent or popular"/>
        <parameter key="limit" value="100"/>
        <parameter key="language" value="en"/>
        <parameter key="until" value="2018.02.04 16:29:29 -0600"/>
        <parameter key="filter_by_geo_location" value="false"/>
        <parameter key="radius_unit" value="miles"/>
      </operator>
      <operator activated="true" class="append" compatibility="8.0.001" expanded="true" height="124" name="Append" width="90" x="447" y="1003">
        <parameter key="datamanagement" value="double_array"/>
        <parameter key="data_management" value="auto"/>
        <parameter key="merge_type" value="all"/>
      </operator>
      <operator activated="true" class="set_macros" compatibility="8.0.001" expanded="true" height="68" name="Set Macros" width="90" x="179" y="442">
        <list key="macros">
          <parameter key="date" value="2017.05.03"/>
          <parameter key="retweetcount" value="20"/>
        </list>
      </operator>
      <operator activated="true" class="social_media:get_twitter_user_statuses" compatibility="7.3.000" expanded="true" height="68" name="Get Twitter User Statuses (4)" width="90" x="112" y="85">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query_type" value="name"/>
        <parameter key="id" value="@generalelectric"/>
        <parameter key="user" value="@generalelectric"/>
        <parameter key="limit" value="100"/>
      </operator>
      <operator activated="true" class="social_media:get_twitter_user_statuses" compatibility="7.3.000" expanded="true" height="68" name="Get Twitter User Statuses (5)" width="90" x="112" y="289">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query_type" value="name"/>
        <parameter key="id" value="@generalelectric"/>
        <parameter key="user" value="@amazon"/>
        <parameter key="limit" value="100"/>
      </operator>
      <operator activated="true" class="social_media:get_twitter_user_statuses" compatibility="7.3.000" expanded="true" height="68" name="Get Twitter User Statuses (6)" width="90" x="45" y="187">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query_type" value="name"/>
        <parameter key="id" value="@generalelectric"/>
        <parameter key="user" value="@IBM"/>
        <parameter key="limit" value="100"/>
      </operator>
      <operator activated="true" class="social_media:get_twitter_user_statuses" compatibility="7.3.000" expanded="true" height="68" name="Get Twitter User Statuses" width="90" x="45" y="34">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query_type" value="name"/>
        <parameter key="user" value="@yahoo"/>
        <parameter key="limit" value="100"/>
      </operator>
      <operator activated="true" class="social_media:get_twitter_user_statuses" compatibility="7.3.000" expanded="true" height="68" name="Get Twitter User Statuses (2)" width="90" x="45" y="391">
        <parameter key="connection" value="TWconnection"/>
        <parameter key="query_type" value="name"/>
        <parameter key="user" value="@google"/>
        <parameter key="limit" value="100"/>
      </operator>
      <operator activated="true" class="append" compatibility="8.0.001" expanded="true" height="166" name="Append (3)" width="90" x="313" y="136">
        <parameter key="datamanagement" value="double_array"/>
        <parameter key="data_management" value="auto"/>
        <parameter key="merge_type" value="all"/>
      </operator>
      <operator activated="true" class="generate_attributes" compatibility="8.0.001" expanded="true" height="82" name="Generate a variable" width="90" x="514" y="85">
        <list key="function_descriptions">
          <parameter key="IMPORTANT-RT" value="if([Retweet-Count]&lt;eval(%{retweetcount}),&quot;Not Important&quot;,&quot;Important&quot;)"/>
        </list>
        <parameter key="keep_all" value="true"/>
      </operator>
      <operator activated="true" class="filter_examples" compatibility="8.0.001" expanded="true" height="103" name="drop text with &quot;RT&quot;" width="90" x="648" y="85">
        <parameter key="parameter_expression" value=""/>
        <parameter key="condition_class" value="custom_filters"/>
        <parameter key="invert_filter" value="true"/>
        <list key="filters_list">
          <parameter key="filters_entry_key" value="Text.contains.RT"/>
        </list>
        <parameter key="filters_logic_and" value="true"/>
        <parameter key="filters_check_metadata" value="true"/>
      </operator>
      <operator activated="true" class="set_role" compatibility="8.0.001" expanded="true" height="82" name="define your &quot;label&quot;" width="90" x="782" y="85">
        <parameter key="attribute_name" value="IMPORTANT-RT"/>
        <parameter key="target_role" value="label"/>
        <list key="set_additional_roles"/>
      </operator>
      <operator activated="true" class="select_attributes" compatibility="8.0.001" expanded="true" height="82" name="Select Attributes (2)" width="90" x="916" y="85">
        <parameter key="attribute_filter_type" value="subset"/>
        <parameter key="attribute" value=""/>
        <parameter key="attributes" value="Text|label|IMPORTANT-RT"/>
        <parameter key="use_except_expression" value="false"/>
        <parameter key="value_type" value="attribute_value"/>
        <parameter key="use_value_type_exception" value="false"/>
        <parameter key="except_value_type" value="time"/>
        <parameter key="block_type" value="attribute_block"/>
        <parameter key="use_block_type_exception" value="false"/>
        <parameter key="except_block_type" value="value_matrix_row_start"/>
        <parameter key="invert_selection" value="false"/>
        <parameter key="include_special_attributes" value="true"/>
      </operator>
      <operator activated="true" class="nominal_to_text" compatibility="8.0.001" expanded="true" height="82" name="Nominal to Text (2)" width="90" x="1050" y="85">
        <parameter key="attribute_filter_type" value="single"/>
        <parameter key="attribute" value="Text"/>
        <parameter key="attributes" value=""/>
        <parameter key="use_except_expression" value="false"/>
        <parameter key="value_type" value="nominal"/>
        <parameter key="use_value_type_exception" value="false"/>
        <parameter key="except_value_type" value="file_path"/>
        <parameter key="block_type" value="single_value"/>
        <parameter key="use_block_type_exception" value="false"/>
        <parameter key="except_block_type" value="single_value"/>
        <parameter key="invert_selection" value="false"/>
        <parameter key="include_special_attributes" value="false"/>
      </operator>
      <operator activated="true" class="extract_macro" compatibility="8.0.001" expanded="true" height="68" name="Extract Macro (2)" width="90" x="1184" y="85">
        <parameter key="macro" value="label_count"/>
        <parameter key="macro_type" value="statistics"/>
        <parameter key="statistics" value="count"/>
        <parameter key="attribute_name" value="IMPORTANT-RT"/>
        <parameter key="attribute_value" value="Important"/>
        <list key="additional_macros"/>
      </operator>
      <operator activated="true" class="multiply" compatibility="8.0.001" expanded="true" height="124" name="Multiply" width="90" x="1318" y="85"/>
      <operator activated="true" class="filter_examples" compatibility="8.0.001" expanded="true" height="103" name="Filter Examples" width="90" x="1251" y="340">
        <parameter key="parameter_expression" value=""/>
        <parameter key="condition_class" value="custom_filters"/>
        <parameter key="invert_filter" value="false"/>
        <list key="filters_list">
          <parameter key="filters_entry_key" value="IMPORTANT-RT.equals.Important"/>
        </list>
        <parameter key="filters_logic_and" value="true"/>
        <parameter key="filters_check_metadata" value="true"/>
      </operator>
      <operator activated="true" class="naive_bayes" compatibility="8.0.001" expanded="true" height="82" name="Naive Bayes" width="90" x="1385" y="391">
        <parameter key="laplace_correction" value="true"/>
      </operator>
      <operator activated="true" class="apply_model" compatibility="8.0.001" expanded="true" height="82" name="Apply Model (2)" width="90" x="1519" y="391">
        <list key="application_parameters"/>
        <parameter key="create_view" value="false"/>
      </operator>
      <operator activated="true" class="performance_classification" compatibility="8.0.001" expanded="true" height="82" name="Performance" width="90" x="1653" y="391">
        <parameter key="main_criterion" value="first"/>
        <parameter key="accuracy" value="true"/>
        <parameter key="classification_error" value="false"/>
        <parameter key="kappa" value="false"/>
        <parameter key="weighted_mean_recall" value="false"/>
        <parameter key="weighted_mean_precision" value="false"/>
        <parameter key="spearman_rho" value="false"/>
        <parameter key="kendall_tau" value="false"/>
        <parameter key="absolute_error" value="false"/>
        <parameter key="relative_error" value="false"/>
        <parameter key="relative_error_lenient" value="false"/>
        <parameter key="relative_error_strict" value="false"/>
        <parameter key="normalized_absolute_error" value="false"/>
        <parameter key="root_mean_squared_error" value="false"/>
        <parameter key="root_relative_squared_error" value="false"/>
        <parameter key="squared_error" value="false"/>
        <parameter key="correlation" value="false"/>
        <parameter key="squared_correlation" value="false"/>
        <parameter key="cross-entropy" value="false"/>
        <parameter key="margin" value="false"/>
        <parameter key="soft_margin_loss" value="false"/>
        <parameter key="logistic_loss" value="false"/>
        <parameter key="skip_undefined_labels" value="true"/>
        <parameter key="use_example_weights" value="true"/>
        <list key="class_weights"/>
      </operator>
      <connect from_op="$GE" from_port="output" to_op="Append" to_port="example set 1"/>
      <connect from_op="$IBM" from_port="output" to_op="Append" to_port="example set 2"/>
      <connect from_op="$AMZN" from_port="output" to_op="Append" to_port="example set 3"/>
      <connect from_op="Get Twitter User Statuses (4)" from_port="output" to_op="Append (3)" to_port="example set 1"/>
      <connect from_op="Get Twitter User Statuses (5)" from_port="output" to_op="Append (3)" to_port="example set 3"/>
      <connect from_op="Get Twitter User Statuses (6)" from_port="output" to_op="Append (3)" to_port="example set 2"/>
      <connect from_op="Get Twitter User Statuses" from_port="output" to_op="Append (3)" to_port="example set 5"/>
      <connect from_op="Get Twitter User Statuses (2)" from_port="output" to_op="Append (3)" to_port="example set 4"/>
      <connect from_op="Append (3)" from_port="merged set" to_op="Generate a variable" to_port="example set input"/>
      <connect from_op="Generate a variable" from_port="example set output" to_op="drop text with &quot;RT&quot;" to_port="example set input"/>
      <connect from_op="drop text with &quot;RT&quot;" from_port="example set output" to_op="define your &quot;label&quot;" to_port="example set input"/>
      <connect from_op="define your &quot;label&quot;" from_port="example set output" to_op="Select Attributes (2)" to_port="example set input"/>
      <connect from_op="Select Attributes (2)" from_port="example set output" to_op="Nominal to Text (2)" to_port="example set input"/>
      <connect from_op="Nominal to Text (2)" from_port="example set output" to_op="Extract Macro (2)" to_port="example set"/>
      <connect from_op="Extract Macro (2)" from_port="example set" to_op="Multiply" to_port="input"/>
      <connect from_op="Multiply" from_port="output 1" to_port="result 1"/>
      <connect from_op="Multiply" from_port="output 2" to_op="Filter Examples" to_port="example set input"/>
      <connect from_op="Multiply" from_port="output 3" to_op="Apply Model (2)" to_port="unlabelled data"/>
      <connect from_op="Filter Examples" from_port="original" to_op="Naive Bayes" to_port="training set"/>
      <connect from_op="Naive Bayes" from_port="model" to_op="Apply Model (2)" to_port="model"/>
      <connect from_op="Apply Model (2)" from_port="labelled data" to_op="Performance" to_port="labelled data"/>
      <connect from_op="Performance" from_port="performance" to_port="result 2"/>
      <portSpacing port="source_input 1" spacing="0"/>
      <portSpacing port="sink_result 1" spacing="0"/>
      <portSpacing port="sink_result 2" spacing="0"/>
      <portSpacing port="sink_result 3" spacing="0"/>
    </process>
  </operator>
</process>
